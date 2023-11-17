# IP Access Constraint

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-redis</artifactId>
</dependency>
```

```java
import com.example.demo.service.IPService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.data.redis.core.StringRedisTemplate;
import org.springframework.http.HttpStatus;
import org.springframework.stereotype.Service;
import org.springframework.web.server.ResponseStatusException;

import javax.servlet.http.HttpServletRequest;
import java.util.concurrent.TimeUnit;

@Service
public class IPServiceImpl implements IPService {
    @Autowired
    StringRedisTemplate stringRedisTemplate;

    /**
     * key过期时间（秒）
     */
    private final Long EXPIRATIONTIME_SECONDS = 30L;

    /**
     * key 前缀，防止和其他地方的key可以冲突
     */
    private final String prefix = "IP:";

    @Override
    public void checkIP(HttpServletRequest request) {
        String ip = request.getHeader("x-forwarded-for");

        if (ip == null || ip.length() == 0 || "unknown".equalsIgnoreCase(ip) || "null".equals(ip)) {
            ip = "" + request.getHeader("Proxy-Client-IP");
        }
        if (ip == null || ip.length() == 0 || "unknown".equalsIgnoreCase(ip) || "null".equals(ip)) {
            ip = "" + request.getHeader("WL-Proxy-Client-IP");
        }
        if (ip == null || ip.length() == 0 || "unknown".equalsIgnoreCase(ip) || "null".equals(ip)) {
            ip = "" + request.getRemoteAddr();
        }

        // 前缀+ip构成key
        String key = prefix + ip;

        //检查key是否存在，返回boolean值
        boolean flag = stringRedisTemplate.hasKey(key);
        if (flag) {
            // 调用次数+1
            stringRedisTemplate.boundValueOps(key).increment(1);
            // 设置过期时间
            stringRedisTemplate.expire(ip, EXPIRATIONTIME_SECONDS, TimeUnit.SECONDS);

            String sumVal = stringRedisTemplate.opsForValue().get(key);
            int sum = Integer.valueOf(sumVal);
            if (sum >= 1) {
                System.out.println("******************"+ ip + " has more than 1 request in 1 minute");
                throw new ResponseStatusException(HttpStatus.BAD_REQUEST, "IP reaches access limit");
            }
        } else {
            // 第一次调用，所以value（调用次数）设置为1
            stringRedisTemplate.opsForValue().set(key, "1", EXPIRATIONTIME_SECONDS, TimeUnit.SECONDS);
        }
    }
}
```