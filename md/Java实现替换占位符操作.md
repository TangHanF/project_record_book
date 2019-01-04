# Java 实现替换占位符操作

## 代码

```java
String printInfo = "这是测试{project}项目而写的{code}代码";
Map<String, String> mapstring = new HashMap<>();
mapstring.put("project", "占位符替换");
mapstring.put("code", "Java");

for (Map.Entry<String, String> entry : mapstring.entrySet()) {
    printInfo = printInfo.replace("{" + entry.getKey() + "}", entry.getValue());
}
System.out.println(printInfo);
```

运行结果：

> 这是测试占位符替换项目而写的Java代码

## 封装方法
```java
/**
 * 占位符替换
 * @param map
 * @param data
 * @return
 */
public static String replaceHolderData(Map<String, String> map, String data) {

    for (Map.Entry<String, String> entry : map.entrySet()) {
        data = data.replace("{" + entry.getKey() + "}", entry.getValue());
    }
    return data;
}
```