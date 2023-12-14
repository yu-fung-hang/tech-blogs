# Time

### Str -> Date + timezone

```
java.time.LocalDateTime ldt = java.time.LocalDateTime.parse(dateStr);
ZoneId zoneId = ZoneId.of("America/Toronto");
ZonedDateTime zdt = ldt.atZone(zoneId);
Date date = Date.from(zdt.toInstant());
```