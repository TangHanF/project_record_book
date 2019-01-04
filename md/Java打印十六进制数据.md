# Java 打印十六进制数据

```java
public static final String nLine = "----------------------------------------------------------------------------";

private static void bytesSet(byte[] inBytes, char fill) {
    if (inBytes.length == 0) {
        return;
    }
    for (int i = 0; i < inBytes.length; i++) {
        inBytes[i] = (byte) fill;
    }
}
public static String trace(byte[] inBytes) {
    int i, j = 0;
    byte[] temp = new byte[76];
    bytesSet(temp, ' ');
    StringBuffer strc = new StringBuffer("");
    strc.append(nLine + "\n");
    for (i = 0; i < inBytes.length; i++) {
        if (j == 0) {
            System.arraycopy(String.format("%03d: ", i).getBytes(), 0, temp, 0, 5);
            System.arraycopy(String.format(":%03d", i + 15).getBytes(), 0, temp, 72, 4);
        }
        System.arraycopy(String.format("%02X ", inBytes[i]).getBytes(), 0, temp, j * 3 + 5 + (j > 7 ? 1 : 0), 3);
        if (inBytes[i] == 0x00) {
            temp[j + 55 + ((j > 7 ? 1 : 0))] = '.';
        } else {
            temp[j + 55 + ((j > 7 ? 1 : 0))] = inBytes[i];
        }
        j++;
        if (j == 16) {
            strc.append(new String(temp)).append("\n");
            bytesSet(temp, ' ');
            j = 0;
        }
    }
    if (j != 0) {
        strc.append(new String(temp)).append("\n");
        bytesSet(temp, ' ');
    }
    strc.append(nLine + "\n");
//		System.out.println(strc.toString());
    return strc.toString();
}

/**
     * 从十六进制字符串到字节数组转换
     * create by GuoF
     *
     * @param hexstr 十六进制形式的字符串
     * @return
     */
    public static byte[] HexString2Bytes(String hexstr) {
        byte[] b = new byte[hexstr.length() / 2];
        int j = 0;
        for (int i = 0; i < b.length; i++) {
            char c0 = hexstr.charAt(j++);
            char c1 = hexstr.charAt(j++);
            b[i] = (byte) ((parse(c0) << 4) | parse(c1));
        }
        return b;
    }

private static int parse(char c) {
        if (c >= 'a')
            return (c - 'a' + 10) & 0x0f;
        if (c >= 'A')
            return (c - 'A' + 10) & 0x0f;
        return (c - '0') & 0x0f;
    }
```

调用：
```java
public static void main(String[] args) {
    String str = "9F2608DAEB4C88899EE36E9F2701809F3704D1DFA2039F360200BA950580800400009A031712259C01009F02060000000000005F2A02084082027C009F1A0208409F03060000000000009F33036048009F34030203009F3501149F101307010103A0A000010A0100000000005F5B0AA0";
    byte[] buf1 = HexString2Bytes(str);
    System.out.println( trace(buf1));
}
```

运行结果：

![](https://ws1.sinaimg.cn/large/006tNc79ly1fyuy9ew6jvj30xi0es0vx.jpg)