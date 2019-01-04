# Java 金额格式化

```java
/**
 * 处理金额。默认处理为#,####.00格式
 *
 * @param amount 金额字符串
 * @return
 */
public static String dealMoney_Full(String amount) {
    NumberFormat nf = NumberFormat.getCurrencyInstance();
    DecimalFormat df = (DecimalFormat) nf;
    df.setMinimumFractionDigits(2);
    df.setMaximumFractionDigits(2);
    df.setDecimalSeparatorAlwaysShown(true);
    String pattern = "##,###.00";
    df.applyPattern(pattern);
    String ret = df.format(Double.parseDouble(amount));
    if (ret.substring(0, 1).equals("."))
        ret = "0" + ret;
    return ret;
}

/**
 * 处理金额。可自定义处理格式，例如：###.00
 *
 * @param amount
 * @param format
 * @return
 */
public static String dealMoney_Full(String amount, String format) {
    NumberFormat nf = NumberFormat.getCurrencyInstance();
    DecimalFormat df = (DecimalFormat) nf;
    df.setMinimumFractionDigits(2);
    df.setMaximumFractionDigits(2);
    df.setDecimalSeparatorAlwaysShown(true);
    String pattern = format;
    df.applyPattern(pattern);
    String ret = df.format(Double.parseDouble(amount));
    if (ret.substring(0, 1).equals("."))
        ret = "0" + ret;
    return ret;
}

```

调用：

```java
System.out.println(CommonUtils.dealMoney_Full("1000"));
System.out.println(CommonUtils.dealMoney_Full("1000.12", "##.00"));
System.out.println(CommonUtils.dealMoney_Full("1000.456"));
```

结果：

1,000.00

1000.12

1,000.46