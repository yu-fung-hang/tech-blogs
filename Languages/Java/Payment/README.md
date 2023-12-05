# Payment

### Dollar to Cent
```
public static Integer dollarToCent(BigDecimal value) {
    if(value == null) return null;
    return value.movePointRight(2).setScale(2, RoundingMode.HALF_UP).intValue();
}
```

### Cent to Dollar
```
private String formatAmount(String n) {
    DecimalFormat decimalFormat = new DecimalFormat("#.00");
    String result = decimalFormat.format(Integer.valueOf(n).doubleValue()/100);

    if(result.charAt(0) == '.') { result = "0" + result; }
    return result;
}
```

```
public static BigDecimal centToDollar(Integer value) {
    if(value == null) return null;
    return new BigDecimal(value).movePointLeft(2).setScale(2, RoundingMode.HALF_UP);
}
```