# Request cases in Controller

```java
import com.fasterxml.jackson.databind.ObjectMapper;
import lombok.Data;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.multipart.MultipartFile;
import org.springframework.web.server.ResponseStatusException;

import javax.servlet.http.HttpServletRequest;
import java.util.TimeZone;

@RestController
@RequestMapping("/api/demo")
public class DemoController {
    @PostMapping("/raw")
    public ResponseEntity<?> method1(@RequestBody PartnerDTO dto) {
        return ResponseEntity.ok(null);
    }

    @PutMapping("/{id}/status/{status}")
    public ResponseEntity<?> method2(@PathVariable Integer id, @PathVariable UserStatus status) {
        return ResponseEntity.ok(null);
    }

    @PostMapping("/x-www-form-urlencoded")
    public ResponseEntity<?> method3(@RequestParam("id") String id, @RequestParam("amount") Integer amount) {
        return ResponseEntity.ok(null);
    }

    // upload files like images
    @PostMapping("/form-data")
    public ResponseEntity<?> method4(@RequestPart("content") String content, @RequestPart(value = "image") MultipartFile image) {
        PartnerDTO dto = readValue(content, PartnerDTO.class);
        return ResponseEntity.ok(dto);
    }

    private static <T> T readValue(String content, Class<T> valueType) {
        try {
            ObjectMapper objectMapper = new ObjectMapper();
            objectMapper.setTimeZone(TimeZone.getDefault());
            return objectMapper.readValue(content, valueType);
        } catch (Exception e) {
            throw new ResponseStatusException(HttpStatus.BAD_REQUEST, "Failed to convert data.");
        }
    }

    // Get client's IP etc.
    @GetMapping("/httpServletRequest")
    public ResponseEntity<?> specialCase(HttpServletRequest request) {
        String ip = request.getRemoteAddr();
        return ResponseEntity.ok(ip);
    }
}

@Data
class PartnerDTO
{
    String appId;
    String apiKey;
}

enum UserStatus {
    enabled, forbidden
}
```

**Note**: `@PathVariable` and `HttpServletRequest` could be shown in all requests.