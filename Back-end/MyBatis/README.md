# MyBatis

## like
```xml
<if test="name != null and name != ''">
    and LOWER(a.name) like CONCAT('%', #{name}, '%')
</if>
```