# JSON

### Transform String into JSON

```xml
<dependency>
    <groupId>org.sharegov</groupId>
    <artifactId>mjson</artifactId>
    <version>1.4.1</version>
</dependency>
```

```java
import mjson.Json;

public class TestJson {
    private void testMethod() {
        Json json = Json.read(response);
        String status = json.at("status").asString();
    }
}
```