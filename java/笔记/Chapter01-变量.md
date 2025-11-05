# 第一章 变量

***String是引用数据类型***

### 一、+的使用

1. 当左右两侧都是数值型时，做加法运算

2. 当左右两边有一方为字符串，做拼接运算

### 二、数据类型

1. 基本数据类型
   
   - 整数类型：byte[1],short[2],int[4],long[8]
   - 浮点类型：float[4],double[8]
   - 字符型：char[2]
   - 布尔型：boolean[1]

2. 引用数据类型
   
   - 类 class
   - 接口 interface
   - 数组 []

3. 整型细节
   
   - byte: -127-128,即-[2^(n*8-1)^-1]~ 2^(n*8-1)^
   - **java中整型常量(具体值)默认为int,声明long型常量须在后面加'l'或'L'**  
      例：`int a = 8L //报错`
   
   - 精度大的类型变小类型报错，反之不会

4. 浮点型细节
   
   - java中浮点型常量（具体值）默认为double,声明float型常量须在后面加'f'或‘F'  
     
      例：`float a = 1.1 //报错`
   
   - 精度大的类型变小类型报错，反之不会
   
   - 浮点数有两种表示形式
   
   - 十进制：5.12，5.0f,.512(必须有小数点)
   
   - 科学计数法：5.12e2[5.12 * 10^2^] (仍是double), 5.12E-2[5.12*10^-2^]
   
   - ***不可直接对两个对运算结果是浮点数的数相等判断***

```java
if(Math.abs(num1 -num2) < 0.00000001) {
}
```

5. 字符型细节
   
   - 字符用'',不能用""
   
   - char本质是数字，可以运算
   
   - 转义字符也是字符，`char c='/n'`
   
   - char型赋值数字时，输出的是数字所对应的字,若要输出数字，则`System.out.println((int)c)`
   
6. 布尔类型细节
   
   - **java不可用0或非0替代false和ture**

## 三、数据类型转换

1. **自动类型转换**
   
   1. 多种类型的数据混合运算时，精度小的类型自动转换为精度大的类型
   
   ```
   double a = 8;
   System.out.println(a)-->8.0
   ```
   
   2. 精度大的类型赋值给精度小的类型报错(**不能把int赋给char**)，反之自动转换
   
   3. (byte,short)和char不会相互转换 
   
   4. **byte,short,char,三者其一参与计算,即使==类型相同==，在计算时首先转换为int**
      
      ```
      byte a = 1;
      short b=1;
      short d = 1;
      short c = a + b;//错误，a+b=>int
      c = b + d;//错误，b+d=>int
      ```
   
   5. 当把数赋给byte时，先判断该数是否在byte范围内，若在则可以
      
      ```
      byte a = 10;//正确
      a = 1000;//错误
      int b = 1;
      a = b; //错误
      ```
   
   6. 运算结果自动提升为操作数中最大的类型

2. **强制类型转换**
   
   1. `int i = (int)1.9;` 
   2. 容量大转换为容量小可能有精度损失或溢出
   3. char可以保存int型常量，不能保存int变量，需要强转

3. **基本数据类型和String类型的转换**
   
   1. 基本类型转String：+ ""
   
      ```
      int n = 100;
      float f = 1.1f;
      bollean t = ture;
      String s1 = n+"";
      String s2 = f+"";
      String s3 = t+"";
      ```
   
   2. String转基本类型：
   
      通过基本类型的包装类调用parseXX方法即可
   
      - 要确保String转为有效的数据，如 "123"可以转为整数，"hello"不行-->parse[分析]
   
        ```
        String s = "123";
        int num1 = Integer.parseInt(s);//123
        double num2 = Double.parseDouble(s);//123.0
        float num3 = Float.parseFloat(s);//123.0
        long num4 = Long.parseLong(s);//123
        byte num5 = Byte.parseByte(s);//123
        boolean b = Boolean.parseBoolean("ture")//true
        ```
   
   3. 将String转为char:  
           `char c = s.charAt(index)`
   
