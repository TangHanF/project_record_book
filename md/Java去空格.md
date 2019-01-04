# Java 去空格

```java
/**
 * 去空格
 * create by GuoF 2015年2月27日00:43:40
 *
 * @param str
 * @return
 */
public static String replaceBlank(String str) {
    Pattern p = Pattern.compile("\\s");
    Matcher m = p.matcher(str);
    String after = m.replaceAll("");
    return after;
}
```