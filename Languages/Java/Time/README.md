# Time

### Str -> Date + timezone

```
java.time.LocalDateTime ldt = java.time.LocalDateTime.parse(dateStr);
ZoneId zoneId = ZoneId.of("America/Toronto");
ZonedDateTime zdt = ldt.atZone(zoneId);
Date date = Date.from(zdt.toInstant());
```

### Handle format like '2023-11-16T22:33:21.508049845'

```
import java.time.LocalDateTime;
import java.time.ZoneId;
import java.time.ZonedDateTime;
import java.util.Date;

public class TestDate {
    public static void main(String[] args) {
        String input = "2023-11-16T22:33:21.508049845";
        System.out.println("Before: " + input);
        parse(input);
    }

    private static void parse(String input) {
        input = input.substring(0, 19);
        LocalDateTime ldt = LocalDateTime.parse(input);
        ZoneId zoneId = ZoneId.of("America/Toronto");
        ZonedDateTime zdt = ldt.atZone(zoneId);
        Date date = Date.from(zdt.toInstant());
        System.out.println("After: " + date);
    }
}
```