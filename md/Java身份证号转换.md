# Java 将15位身份证号转化为18位返回，非15位身份证号原值返回

```java
/* 
身份证号码的结构和表示形式<br> 
1、号码的结构<br> 
   公民身份号码是特征组合码，由十七位数字本体码和一位校验码组成。排列顺序从左至右依次为：六位数字地址码，八位数字出生日期码，三位数字顺序码和一位数字校验码。<br> 
2、地址码<br> 
   表示编码对象常住户口所在县(市、旗、区)的行政区划代码，按GB/T2260的规定执行。<br> 
3、出生日期码<br> 
   表示编码对象出生的年、月、日，按GB/T7408的规定执行，年、月、日代码之间不用分隔符。<br> 
4、顺序码<br> 
   表示在同一地址码所标识的区域范围内，对同年、同月、同日出生的人编定的顺序号，顺序码的奇数分配给男性，偶数分配给女性。<br> 
5、校验码<br> 
 （1）十七位数字本体码加权求和公式<br> 
      S = Sum(Ai * Wi), i = 0, ... , 16 ，先对前17位数字的权求和<br> 
      Ai:表示第i位置上的身份证号码数字值<br> 
      Wi:表示第i位置上的加权因子<br> 
      Wi: 7 9 10 5 8 4 2 1 6 3 7 9 10 5 8 4 2<br> 
 （2）计算模<br> 
      Y = mod(S, 11)<br> 
 （3）通过模得到对应的校验码<br> 
      Y: 0 1 2 3 4 5 6 7 8 9 10<br> 
         校验码: 1 0 X 9 8 7 6 5 4 3 2<br> 
*/  
/** 
 * 将15位身份证号转化为18位返回，非15位身份证号原值返回 
 * @author InJavaWeTrust 
 * 
 */  
public class Ic {  
      
    /** 
     * 将15位身份证号转化为18位返回，非15位身份证号原值返回 
     * @param identityCard 
     * @return 
     */  
    public static String get18Ic(String identityCard) {  
        String retId = "";  
        String id17 = "";  
        int sum = 0;  
        int y = 0;  
        // 定义数组存放加权因子（weight factor）  
        int[] wf = { 7, 9, 10, 5, 8, 4, 2, 1, 6, 3, 7, 9, 10, 5, 8, 4, 2 };  
        // 定义数组存放校验码（check code）  
        String[] cc = { "1", "0", "X", "9", "8", "7", "6", "5", "4", "3", "2" };  
        if (identityCard.length() != 15) {  
            return identityCard;  
        }  
        // 加上两位年19  
        id17 = identityCard.substring(0, 6) + "19" + identityCard.substring(6);  
        // 十七位数字本体码加权求和  
        for (int i = 0; i < 17; i++) {  
            sum = sum + Integer.valueOf(id17.substring(i, i + 1)) * wf[i];  
        }  
        // 计算模  
        y = sum % 11;  
        // 通过模得到对应的校验码 cc[y]  
        retId = id17 + cc[y];  
        return retId;  
    }  
      
    public static void main(String[] args) {  
        // 例子 511702800222130  
        System.out.println(get18Ic("511702800222130"));  
        // 结果 511702198002221308  
    }  
  
}  
```