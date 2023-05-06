# Get Client's IP

```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import javax.servlet.http.HttpServletRequest;

@RestController
public class IPController
{
   @GetMapping("ip")
   public String getClientIP(HttpServletRequest request)
   { return request.getRemoteAddr(); }
}
```

**Url**: http://your-host:8080/ip

**Http method**: GET