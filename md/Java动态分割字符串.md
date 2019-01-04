# Java 根据长度描述动态分割字符串

```java
public static List<String> splitStrDIY(String dataStr, int[] lenArr) {
    StringBuffer stringBuffer = new StringBuffer(dataStr);
    List list = new ArrayList();
    int index = 0;
    for (int i = 0; i < lenArr.length; i++) {
        String tmpStr = stringBuffer.substring(index, lenArr[i] + index);
        list.add(tmpStr);
        index += lenArr[i];
    }

    return list;
}
```