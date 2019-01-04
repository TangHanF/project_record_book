# Java 字节数组分割

```java
/**
 * 分割byte[]数组
 * 作者：GuoF
 *
 * @param sourceByte 要分割的byte数组
 * @param startIndex 分割起始位置（常规意义）
 * @return byte[] 返回分割之后的数组
 */
public static byte[] subByteArray(byte[] sourceByte, int startIndex) {
    byte[] tmpByte = new byte[sourceByte.length - startIndex];
    System.arraycopy(sourceByte, startIndex, tmpByte, 0, tmpByte.length);
    return tmpByte;
}

/**
 * 分割byte[]数组
 * 作者：GuoF
 *
 * @param sourceByte 要分割的byte数组
 * @param startIndex 分割起始位置（常规意义）
 * @param length     分割长度
 * @return byte[] 返回分割之后的数组
 */
public static byte[] subByteArray(byte[] sourceByte, int startIndex, int length) {
    byte[] tmpByte = new byte[sourceByte.length - startIndex];
    System.arraycopy(sourceByte, startIndex, tmpByte, 0, length);
    return tmpByte;
}

public static byte[] subByteArray(byte[] sourceByte, int bufferLen, int startIndex, int length) {
    byte[] tmpByte = new byte[bufferLen];
    System.arraycopy(sourceByte, startIndex, tmpByte, 0, length);
    return tmpByte;
}
```