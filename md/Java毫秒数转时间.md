# Java 毫秒数转时间

```java
/**
 * 将毫秒数转为对应的时间
 * @param timeMillis 毫秒数
 * @param formate 时间格式，例如：HH:mm:ss
 * @return
 */
public static String convertTimeMillis(long timeMillis, String formate) {
    SimpleDateFormat simpleDateFormat = new SimpleDateFormat(formate);
    simpleDateFormat.setTimeZone(TimeZone.getTimeZone("GMT+00:00"));
    String res = simpleDateFormat.format(timeMillis);
    return res;
}
```

调用：
```java
long ms = 300000;
System.out.println(CommonUtils.convertTimeMillis(ms,"HH:mm:ss"));
```

结果：

00:05:00