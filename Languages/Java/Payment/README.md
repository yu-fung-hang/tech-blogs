# Payment

### Dollar to Cent
```
BigDecimal bdAmount = new BigDecimal(bill.getAmount());
bdAmount = bdAmount.movePointRight(2).longValue();
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