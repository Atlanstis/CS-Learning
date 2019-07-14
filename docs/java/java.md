
## Java ���

### Java �汾

- Java SE��Standard Edition����׼�棬������׼�� JVM �ͱ�׼�⣬������Javaƽ̨�ĺ��ġ�

- Java EE��Enterprise Edition����ҵ�棬��Java SE�Ļ����ϼ����˴�����API�Ϳ⣬�Ա㷽�㿪��WebӦ�á����ݿ⡢��Ϣ����ȡ�

- Java ME��Micro Edition�����Ƕ��ʽ�豸�ġ�����桱����������Ϳⶼ�� Java EE��ͬ��

  <div align="center">
      <img src="pics/1562896856294.png" width="300px">
  </div>

### ���ʽ���

- JDK��Java Development Kit������ JRE �� Java �Ŀ������ߣ����������������ȣ���

- JRE��Java Runtime Environment������ Java �ֽ�����������

  <div align="center">
      <img src="pics/1562897337667.png" width="400px">
  </div>

### ��װ JDK

[Oracle ��������](https://www.oracle.com/technetwork/java/javase/downloads/index.html)

��װ��ɺ����û���������

#### ���û�������

`JAVA_HOME=%��װ·��%\Java|jdk` 

JAVA_HOME ָ��JDK�İ�װĿ¼��Eclipse/Tomcat �� JAVA ���������ͨ������ JAVA_HOME �������ҵ���ʹ�ð�װ�õ� JDK��

`PATH=%JAVA_HOME%\bin`

PATH ָ����������·����bin ·���°����˳��õĿ�ִ���ļ����� javac/ java �ȡ�

`CLASSPATH:.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar `

CLASSPATHָ��������·������import, package �ؼ����йء�

�����óɹ�����������`java -version`����õ����������

```
$ java -version
java version "11.0.2" 2019-01-15 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.2+9-LTS)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.2+9-LTS, mixed mode)
```

PATH �µĳ��ÿ�ִ���ļ�

- javac������ Java �� **������** �������ڰ� Java Դ���ļ�����`.java`��׺��β������Ϊ Java �ֽ����ļ����� `.class` ��׺��β����
- java������ JVM�������� Java ������ JVM ִ��ָ�� Java �ֽ����ļ���
- jar�����ڰ�һ�� `.class `�ļ������һ�� `.jar` �ļ������ڷ�����
- javadoc�����ڴ�JavaԴ�����Զ���ȡע�Ͳ������ĵ���
- jdb��Java �����������ڿ����׶ε����е��ԡ�

#### ���� Java ����

1. ���ı��༭�������� Java ���룬����Ϊ `����.java` �ĸ�ʽ

2. ʹ�� `javac` ���Խ� `.java` Դ������ `.class`�ֽ��룻

   ```
   $ javac Hello.java
   ```

3. ʹ�� `java` ����һ���ѱ���� Java ���򣬲�����������

   ```
   $ java Hello
   Hello, world!
   ```

#### IDE

IDE�Ǽ��ɿ������� (Integrated Development Environment) ����д�����԰ѱ�д���롢��֯��Ŀ�����롢���С����Եȷŵ�һ�����������У��ܼ������߿���Ч�ʡ�

����ʹ�� Eclipse ��

## Java �������

�������͵ı����ǡ����С�ĳ����ֵ��ֻ��ʾ�򵥵��ַ������֣�JVM ��Ϊ�������������ʵ��ռ�õ��ڴ�ռ䡣

�������͵ı����ǡ�ָ��ĳ�����󣬿��Ա�ʾ���ӵ��������ͣ���ָ�����ĳ��ʵ����ָ�롣

Java���ַ����� `char` �ǻ������ͣ��ַ������� `String` ���������͡�

### ��������

| �������� | λ�� / bit | Ĭ��ֵ    | ����ֵ           | ��װ����  |
| -------- | ---------- | --------- | ---------------- | --------- |
| boolean  | 1          | false     | true, false      | Boolean   |
| byte     | 8          | 0         | all byte value   | Byte      |
| char     | 16         | �� u0000 ' | \u0000 to \u007F | Character |
| short    | 16         | 0         | -128 \~ 127       | Short     |
| int      | 32         | 0         | -128 \~ 127       | Interger  |
| long     | 64         | 0 L       |                  | Long      |
| float    | 32         | 0.0 f     |                  | Float     |
| double   | 64         | 0.0       |                  | Double    |

#### �����

�ο�[IntegerCache](https://blog.csdn.net/weixin_40243894/article/details/81279762)

Integer�ڲ�ά����IntegerCache��һ���ڲ��࣬IntegerCache��һ����̬��Integer���飬�����СĬ��Ϊ **[-128,127]** ���������ʱ�ͽ�-128 �� 127 ��Integer���󴴽��ˣ���������cache�����С�

- `new Integer(1)` ÿ�ζ����½�һ������
- `Integer.valueOf(1)` �����ж�ֵ�Ƿ��ڻ�����У�������ֱ�ӷ��ػ���ֵ
- `Integer x = 1` ���Զ�װ�䣬�������������Զ�װ������е��� valueOf() ����

```java
//IntegerCache��СĬ��Ϊ[-128,127]
Integer x = 1;//�Զ�װ��
Integer y = 1;
System.out.println(String.format("1:%s",x == y));// ture�����û���ض���
x = 127;
y = 127;
System.out.println(String.format("2:%s",x == y));// ture�����û���ض���
x = 128;
y = 128;
System.out.println(String.format("3:%s",x == y));// false������127���½�������ͬ��Integer����
//�������־��棬���캯�� Integer(int) �� java9 ֮��Ͳ��Ƽ�ʹ����
Integer x1 = new Integer(1);
Integer y1 = new Integer(1);
System.out.println(String.format("4:%s",x1 == y1));// false��new Intege�����½�����������
x1 = Integer.parseInt("127");
y1 = Integer.parseInt("127");
System.out.println(String.format("5:%s",x1 == y1));// ture, parstInt()�������ص���int��������,�Զ�װ�䣬�ͱ����Integer x = 127,������valueOf����
x1 = Integer.parseInt("128");
y1 = Integer.parseInt("128");
System.out.println(String.format("6:%s",x1 == y1));// false������127    
Integer x2 = Integer.valueOf(1);
Integer y2 = Integer.valueOf(1);
System.out.println(String.format("7:%s",x2 == y2));	//true�����û�����е�ͬһ����
```

### ��������

#### String

##### null �Ϳ��ַ���

`String a = null` ������һ���ַ������͵����ã���ָ��Ϊnull������û��ָ���κε��ڴ�ռ䡣 
`String s = ""` ������һ���ַ������͵����ã���ֵΪ ���� ���ַ�������� s ����ָ����ǿ��ַ������ڴ�ռ䡣

##### [�ж��ַ����Ƿ�Ϊ�գ�](https://blog.csdn.net/wilson_m/article/details/79120347 )

`if (s == null || s.length() == 0);  `

��� String ����Ϊ null , ��ȥ���� length() �Ȳ������׳� java.lang.NullPointerException��������Ҫ�ж� s == null ����˳����������ǰ�档

##### �ַ������ɱ�

String �౻����Ϊ final�����ɼ̳С�Java 9 ֮�󣬸��� byte ���͵� value ����洢�ַ�����value ���鱻����Ϊ final����û�иı� value ����ķ�������֤�� String ���ɱ䡣

```java
public class Main {
    public static void main(String[] args) {
        String s = "hello";//�ַ������� s ָ��"hello"
        String t = s;//t = "hello"
        s = "world";//s = "world"
        System.out.println(t); // t = "hello"
    }
}
```

[���ɱ�ĺô�](<https://cyc2018.github.io/CS-Notes/#/notes/Java%20%E5%9F%BA%E7%A1%80?id=%e4%b8%8d%e5%8f%af%e5%8f%98%e7%9a%84%e5%a5%bd%e5%a4%84>)

- ���Ի��� hash ֵ
- String Pool ����Ҫ
- ��ȫ��
- �̰߳�ȫ

##### String��StringBuilder��StringBuffer

- String�����ɱ䣬�̰߳�ȫ
- StringBuilder���ɱ䣬�����̰߳�ȫ��
- StringBuffer���ɱ䣬�̰߳�ȫ���ڲ�ʹ��synchronized����ͬ��

##### [String Pool](<https://www.jianshu.com/p/f3dbe3d57680>)

**new �������ڶ��ϴ�������������** 

`new String("aaa")` 

- ϵͳ�����ַ�������������Ѱ���Ƿ���һ��"abc"���ַ�����

- ����еĻ������ڶ��и���һ�����ַ��������ҽ����е�����ָ��s,���ʱ��ϵͳֻ������һ�����󣬼� **���еĶ���** ��

- ���û�еĻ�����������ַ������������ȴ���һ���ַ���Ϊ"abc"�ĳ�����Ȼ���ٸ��Ƶ������棬��󽫶����ڵĵ�ַָ��s�����ʱ�򴴽�����������

`String s = "bbb";` 

- ϵͳ�����ַ�����Ѱ���Ƿ����"abc"�ĳ���
- ������ڣ���ֱ�ӽ���"abc"�ڳ������еĵ�ַָ��s�����ʱ��ϵͳû�д����¶���
- ��������ڣ����ڳ��������½�һ��"abc"�����볣�������棬Ȼ���ٷ��ظõ�ַ�����ʱ��ϵͳ������һ������

`s.intern()` 

- ��� String Pool ���Ѿ�����һ���ַ����� s ���õ��ַ���ֵ��ȣ�ʹ�� equals() ��������ȷ��������ô�ͻ᷵�� String Pool ���ַ��������ã�
- ������ String Pool �����һ���µ��ַ�����������������ַ��������á�

[ʾ��](<https://cyc2018.github.io/CS-Notes/#/notes/Java%20%E5%9F%BA%E7%A1%80?id=string-pool>)

```java
String s1 = new String("aaa");
String s2 = new String("aaa");
System.out.println(s1 == s2);  // false
String s3 = s1.intern();
String s4 = s1.intern();
System.out.println(s3 == s4);  // true
String s5 = "bbb";
String s6 = "bbb";
System.out.println(s5 == s6);  // true
```

#### ����

����һ�������󣬴�С�Ͳ��ɱ䣻����Ԫ�ؿ�����ֵ���ͣ���int�����������ͣ���String���������鱾�����������ͣ�

```java
//����Ԫ��Ϊֵ����
ns = new int[] { 68, 79, 91, 85, 62 };
```

![1562911998948](E:\GitHub\CS-Learning\docs\java\pics\1562911998948.png)

```java
//����Ԫ��Ϊ��������
String[] names = {
    "ABC", "XYZ", "zoo"
};
```

![1562912100211](E:\GitHub\CS-Learning\docs\java\pics\1562912100211.png)

###  �ؼ��� 

- var ����ʡ�Ա�������

  ```java
  var sb = new StringBuilder();
  //���������Զ��ж�Ϊ��������
  StringBuilder sb = new StringBuilder();
  ```


### ��������

#### ���

���������������˷�Χ���ͻ�������������� **�������** ������õ�һЩ��ֵĴ𰸡�

������Ҫ�˽�[���롢����](<https://www.cnblogs.com/flowerslip/p/5933833.html>)

���������� = ���� =ԭ��

���������� = ԭ�루����λ���䣩����λȡ��

?	    ���� = ���� + 1

��Сֵ�����������

�� byte Ϊ����һ���ֽڣ�8 bit��ȡֵ��Χ�� -128 \~ 127������ **-128ֻ�в���**  **��1000 0000��**

#### �������

##### ����/�Լ�

`++n` ��ʾ�ȼ� 1 ������ n��`n++` ��ʾ������ n �ټ� 1��

##### ��λ����

<< : ���������������λ������num << 1,�൱�� num ����2

\>> : ���������������λ������num >> 1,�൱�� num ����2

\>>> : �޷������ƣ����Է���λ����λ����0����

[��λ����ȳ˳���������ܸ���](<https://blog.csdn.net/zhou_zhou_gogo1/article/details/84246328>)������ 2^k^ �ĳ˳����������ת��Ϊ��λ���㡣

���������� 0 ȡ�������������� ��ȡ����������ʾ���������� a�����ý��һ�������ڸ��� b������ǲ�ͬ�ġ�

```java
    public static void main(String[] args) {
        int a = 7;
        int b = -7; 
        int a1 = a >> 1;
        int b1 = b >> 1;
        System.out.println("a / 2 = " + a/2);//a / 2 = 3
        System.out.println("a >> 1 = " + a1 );//a >> 1 = 3
        System.out.println("b / 2 = " + b/2);//b / 2 = -3
        System.out.println("b >> 1 = " + b1 );//b >> 1 = -4        
    }
```

##### �߼������

&���룩��&&����·�룩��|���򣩣�||����·�򣩣�^�����

���������һ����Ҫ�ص��� **��·����** �����һ����������ı��ʽ����ǰȷ�������������ļ��㲻��ִ�У�ֱ�ӷ��ؽ����

��Ϊ`false && x`�Ľ������`false`������`x`��`true`����`false`����ˣ���������ȷ����һ��ֵΪ`false`�󣬲��ټ������㣬����ֱ�ӷ���`false`��

### �������

#### ���

`print` ��ʾ����󲻻��У�

`println` ��print line����д����ʾ��������У�

`printf`��ʾ��ʽ�������ͨ��ʹ��ռλ��`%?`���Ѻ���Ĳ�����ʽ����ָ����ʽ��

Eclipse ������ syso ,�ٰ� alt + '/' �ɿ������� System.out.println( ) ��

| ռλ�� | ˵��                             |
| :----- | :------------------------------- |
| %d     | ��ʽ���������                   |
| %x     | ��ʽ�����ʮ����������           |
| %f     | ��ʽ�����������                 |
| %e     | ��ʽ�������ѧ��������ʾ�ĸ����� |
| %s     | ��ʽ���ַ���                     |

#### ����

[java�дӼ�����������ַ���](<https://blog.csdn.net/u012249177/article/details/49586383>)

1. System.in �� System.out ����
2. InputStreamReader �� BufferedReader ����
3. Scanner ���еķ���������Ҫ����һ�� Scanner �����ٵ��÷�����

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in); // ����Scanner����
        String name = scanner.nextLine(); // ��ȡһ�����벢��ȡ�ַ���
        int age = scanner.nextInt(); // ��ȡһ�����벢��ȡ����
    }
}
```

### if �ж�

#### ���������ж�

�������ڼ�����г����޷���ȷ��ʾ�����Ҽ�����ܳ�������ˣ��жϸ�������Ȳ���ֱ���� `==` �жϡ���ȷ�ķ��������ò�ֵС��ĳ���ٽ�ֵ���жϣ�

```java
public class Main {
    public static void main(String[] args) {
        double x = 1 - 9.0 / 10;
        if (Math.abs(x - 0.1) < 0.00001) {
            System.out.println("x is 0.1");
        } else {
            System.out.println("x is NOT 0.1");
        }
    }
}
```

#### �ж������������

`==` ��ʾ���������Ƿ�ָ�� **ͬһ������** ��

`equals()` �����ж��������͵� **��������** �Ƿ���ȡ�

ע�⣺ִ����� `s1.equals(s2)` ʱ��������� `s1` Ϊ `nul ` ���ᱨ `NullPointerException` ��

```java
//��ȷ���������� s1 != null
public class Main {
    public static void main(String[] args) {
        String s1 = null;
        if (s1 != null && s1.equals("hello")) {
            System.out.println("hello");
        }
    }
}

```

### switch

`case` ������ ����͸�ԡ� ��©д `break` ��������ص��߼����󣬶��Ҳ�����Դ�����з��ִ��󡣴� Java 12 ��ʼ��`switch` �������Ϊ�����ı��ʽ�﷨��ʹ������ģʽƥ�䣨Pattern Matching���ķ�������ֻ֤��һ��·���ᱻִ�У�û�д�͸ЧӦ���ʲ���Ҫ `break` ��䣺

```java
public class Main {
    public static void main(String[] args) {
        String fruit = "apple";
        switch (fruit) {
        case "apple" -> System.out.println("Selected apple");
        case "pear" -> System.out.println("Selected pear");
        case "mango" -> {
            System.out.println("Selected mango");
            System.out.println("Good choice!");
        }//��������� {} ������
        default -> System.out.println("No fruit selected");
        }
    }
}
```

## �������

### ����

��װ�ԣ����ض�������Ժ�ʵ��ϸ�ڣ�ֻ�ṩ�������ʷ�ʽ

```java
public class Main {
    public static void main(String[] args) {
        Person ming = new Person();
        ming.setBirth(2008);
        System.out.println(ming.getAge());
    }
}

class Person {
    private String name;//�ⲿ�޷�����
    private int birth;//�ⲿ�޷�����

    public void setBirth(int birth) {
        this.birth = birth;
    }

    public int getAge() {
        return calcAge(2019); // ����private����
    }

    // private�������ⲿ�޷�����
    private int calcAge(int currentYear) {
        return currentYear - this.birth;
    }
}
```

### ���췽��

���췽�������ƾ������������췽���Ĳ���û�����ƣ��ڷ����ڲ���Ҳ���Ա�д������䡣���ǣ�����ͨ������ȣ����췽��û�з���ֵ��Ҳû�� `void` �������ù��췽���������� `new` ��������

���һ����û�ж��幹�췽�������������Զ�Ϊ��������һ��Ĭ�Ϲ��췽������û�в�����Ҳû��ִ����䡣

����ͬʱ���ڶ�����췽���������� **����** ��

```java
class Person {
	//Ĭ�ϵĹ��췽��
    public Person() {
    }
    //�Զ��幹�췽��
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

### ��������д

#### ����

������ͬһ�����У�ָһ���������Ѿ����ڵķ�����������ͬ�����ǲ������͡�������˳��������һ����ͬ��

Ӧ��ע����ǣ�����ֵ��ͬ����������ͬ���������ء�

#### ��д

�����ڼ̳���ϵ�У�ָ����ʵ����һ���븸���ڷ�����������ȫ��ͬ��һ��������

Ϊ��������ʽ�滻ԭ����д�������������ƣ�

- ���෽���ķ���Ȩ�ޱ�����ڵ��ڸ��෽����
- ���෽���ķ������ͱ����Ǹ��෽���������ͻ�Ϊ�������͡�
- ���෽���׳����쳣���ͱ����Ǹ����׳��쳣���ͻ�Ϊ�������͡�

ʹ�� @Override ע�⣬�����ñ�������æ����Ƿ������������������������

### �̳�

�κ��࣬���� `Object`������̳���ĳ���࣬δ��ȷע�� `extends` ���࣬���������Զ����� `extends Object`��

�κ�`class`�Ĺ��췽������һ���������ǵ��ø���Ĺ��췽�������û����ȷ�ص��ø���Ĺ��췽������������������Զ���һ��`super();`

���಻��̳��κθ���Ĺ��췽��������Ĭ�ϵĹ��췽���Ǳ������Զ����ɵģ����Ǽ̳еġ�

### ��̬

������Ը�д����ķ�����Override������д�������иı��˸��෽������Ϊ��

Java ��ʵ�����������ǻ��� **����ʱ��ʵ�����͵Ķ�̬����** �����Ǳ������������͡�

```java
public class Main {
    public static void main(String[] args) {
    //��������Ϊ Person��ʵ������Ϊ Student
    	Person p = new Student();
        p.run(); // ��ӡStudent.run
    }
}

class Person {
    public void run() {
        System.out.println("Person.run");
    }
}

class Student extends Person {
    @Override
    public void run() {
        System.out.println("Student.run");
    }
}
```

**��̬�����ԣ������ڲ��ܶ�̬�������õ����෽����** 

```java
//�޷�ȷ��������� p ��ʵ�������� Person ���� Student 
public void runTwice(Person p) {
    //�޷�ȷ�����õ����ĸ���� run()����
    p.run();
    p.run();
}
```

### ������

�������ķ���������Ҫʵ���κι��ܣ�������Ϊ�˶��巽��ǩ����Ŀ����������ȥ��д������ô�����԰Ѹ���ķ�������Ϊ���󷽷���

```java
class Person {
    public abstract void run();
}
```

ʹ�� `abstract` ���ε�����ǳ����ࡣ�����޷�ʵ����һ�������࣬�����౾����Ƴ�ֻ�����ڱ��̳С�

ͨ�� `abstract` ����ķ����ǳ��󷽷�����ֻ�ж��壬û��ʵ�֡����󷽷��������������ʵ�ֵĽӿڹ淶��

ͨ��`abstract`����ķ����ǳ��󷽷�����ֻ�ж��壬û��ʵ�֣����ܱ�ʵ���������󷽷��������������ʵ�ֵĽӿڹ淶��

```java
public class Main {
    public static void main(String[] args) {
        Person p = new Student();
        p.run();
    }
}

abstract class Person {
    public abstract void run();
}

class Student extends Person {
    @Override
    public void run() {
        System.out.println("Student.run");
    }
}
```

#### ���������

��һ�����ø߲����ͣ���������ʵ�������͵ķ�ʽ��

- �ϲ����ֻ����淶�����磺`abstract class Person`����
- �����ҵ���߼��ɲ�ͬ������ʵ�֣������߲������ġ�
- ֻ���ĳ��󷽷��Ķ��壬����������ľ���ʵ�֡�

```java
Person s = new Student();
// ������Person�����ľ���������:
s.run();
```

### �ӿ�

�ӿ��в������ֶΣ�����ķ���Ĭ�϶��� `public abstract` ��

һ����ֻ�ܼ̳���һ���࣬������ʵ�ֶ���ӿڣ�ʹ�ùؼ��� `implements` ��

һ���ӿڿ��Լ̳���һ���ӿڣ�ʹ�ùؼ��� `extends` ��

```java
interface Hello {
    void hello();
}
//һ���ӿڼ̳���һ���ӿ�, extends
interface Person extends Hello {
    void run();
}
//һ����ʵ�ֶ���ӿ�,implements
class Student implements Person, Hello {
    private String name;

    public Student(String name) {
        this.name = name;
    }

    @Override
    public void hello() {
        System.out.println(this.name + " hello");
    }
    
    @Override
    public void run() {
        System.out.println(this.name + " run");
    }
    
}
```

�������֣�Java �Ľӿ���ָ `interface` �Ķ��壬��ʾһ���ӿ����ͺ�һ�鷽��ǩ��������̽ӿڷ�ָ�ӿڹ淶���緽��ǩ�������ݸ�ʽ������Э��ȡ�

####  **[default����](<https://blog.csdn.net/qq_35835624/article/details/80196932>)** 

�� JDK 1.8 ֮�󣬽ӿڿ��Զ��� `default` ������ʵ������Բ��ظ�д`default` ��������ͬʱ�̳е������ӿ��ж���������ͬ `default` ��������֪�������ĸ��ӿ��е� `default` ��������Ҫ��ʵ����������ʵ�ָ÷��������̳еĸ����һ���ӿ��ж�����ͬһ����������ʱ��ʵ������ø���ķ�������Ϊ **�������ڽӿ�** ��

`default`�����ͳ��������ͨ������������ͬ�ġ���Ϊ`interface`û���ֶΣ�`default`�����޷������ֶΣ������������ͨ�������Է���ʵ���ֶΡ�

### ��̬�ֶκ;�̬����

#### ��̬�ֶ�

```java
class Person {
    //����ʵ���ֶ� name:
    public String name;
    // ���徲̬�ֶ� number:
    public static int number;
}
```

- ʵ���ֶΣ��� class �ж�����ֶΣ�ÿ��ʵ�����ж������ֶΣ�����ʵ����ͬ���ֶλ���Ӱ�졣
- ��̬�ֶΣ��� `static` ���ε��ֶΣ�����ʵ������ͬһ����̬�ֶΡ��޸�һ��ʵ���ľ�̬�ֶΣ���ı�����ʵ���ľ�̬�ֶΣ���Ϊ�����϶���ͬһ���ֶΡ�
- ���Ƽ��� `ʵ������.��̬�ֶ�` (hong.number) ȥ���ʾ�̬�ֶΣ���Ϊ��Java�����У�ʵ������û�о�̬�ֶΣ��Ƽ��� `����.��̬�ֶ�` (Person.number) �����ʡ��Ѿ�̬�ֶ����Ϊ���� `class` ������ֶΣ���ʵ���ֶΣ���

```java
public class Main {
    public static void main(String[] args) {
        Person ming = new Person("Xiao Ming", 12);
        Person hong = new Person("Xiao Hong", 15);
        ming.number = 88;
        System.out.println(hong.number);//88
        hong.number = 99;
        System.out.println(ming.number);//99
    }
}

class Person {
    public String name;
    public int age;

    public static int number;//��̬����

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

#### ��̬����

�� `static` ���εķ���

����ʵ����������ͨ��һ��ʵ�������������þ�̬����ֱ��ͨ�������Ϳ��Ե��á�

��Ϊ��̬��������`class`��������ʵ������ˣ���̬�����ڲ����޷�����`this`  ������Ҳ�޷�����ʵ���ֶΣ���ֻ�ܷ��ʾ�̬�ֶΡ�

```java
public class Main {
    public static void main(String[] args) {
        //ֱ��ͨ�� ����.������ ���þ�̬����
        Person.setNumber(99);
        System.out.println(Person.number);
    }
}

class Person {
    public static int number;
    //��̬����
    public static void setNumber(int value) {
        number = value;
    }
}
```

#### �ӿڵľ�̬�ֶ�

�ӿڲ��ܶ���ʵ���ֶΣ��������о�̬�ֶΣ�Ĭ��Ϊ `public static final` ���͡�

### ��

Java�ڽ���`package`������Ϊ�˱���`class`������ͻ��

JDK�ĺ�����ʹ��`java.lang`�������������Զ����룻

JDK�����������ඨ����`java.util.*`��`java.math.*`��`java.text.*`��������

�����Ƽ�ʹ�õ��õ�����������`org.apache`��

### ������

һ��`.java`�ļ�ֻ�ܰ���һ��`public`�࣬�����԰��������`public`�ࡣ�����`public`�࣬�ļ��������`public`���������ͬ��

[Java����������](https://blog.csdn.net/bupa900318/article/details/80555929)
[Java�����Ͷ����������](https://www.cnblogs.com/AlanLee/p/6627949.html)

#### �༶������ȫ�ֱ�������̬������
��Ҫʹ��static�ؼ������Ρ��༶�������ඨ�����Ѿ����ڣ�ռ���ڴ�ռ䣬����ͨ�����������ʣ�����Ҫʵ������
#### ����ʵ������������Ա������
ʵ������Ż�����ڴ�ռ䣬���ܷ��ʡ���Ա�����Ƕ����ڷ���֮�⣬��֮�ڵġ���Ա�������Ŷ���Ĵ��������ڣ����Ŷ������ʧ����ʧ��
#### �������������ֲ�������
�ֲ������ڵ����˶�Ӧ�ķ�����ִ�е��˴����ñ��������ʱ���ڣ��ֲ�����������������������ĵ㿪ʼ��һ�������Լ������������ϴ��ڴ�����ʧ��
#### �鼶����
������һ�����ڲ��ı������������������ھ�������飬������������ʧ�ˣ����� if��for ���Ŀ顣����ָ�ɴ����Ű�Χ�Ĵ��롣
#### ����˵��
- �����ڲ������ܷ��ʷ������ı����������Է����༶��ʵ�����ı���
- ���ڲ��ܹ������༶��ʵ��������������鱻�����ڷ����ڲ����������Է��ʷ������ı���
- �༶�����ͳ�Ա��������Ĭ�ϵĳ�ʼֵ
- �������Ϳ鼶�ı���û��Ĭ�ϵĳ�ʼֵ�����뱻��ʾ�س�ʼ���������ܷ���

## Java ������

### ƴ���ַ���

`StringJoiner (CharSequence delimiter, CharSequence prefix,  CharSequence suffix)` �ĵڶ����͵����������ֱ���ƴ�Ӻ���ַ�����ǰ׺�ͺ�׺��

### ��װ��

��װ���� **��������** ���� final ����������**���ɱ���**��

�ڱ������Զ�����Զ�װ����Զ����䣻�����͸������İ�װ���Ͷ��̳��� `Number`��

### JavaBean

�������������淶�� class ��Ϊ JavaBean

- ����`private`ʵ���ֶΣ�
- ͨ��`public`��������дʵ���ֶΡ�

```java
public class Person {
    private String name;
    private int age;

    public String getName() { return this.name; }
    public void setName(String name) { this.name = name; }

    public int getAge() { return this.age; }
    public void setAge(int age) { this.age = age; }
}
```

### ö����

Java ʹ�� `enum` ����ö�����ͣ���������������Ϊ `final class Xxx extends Enum { �� }`�������Ͼ��� class

���������ͣ�����ʵ������ͨ�� new ������ֻ��ͨ�����·�ʽ����ʵ����

```java
enum Weekday {
    SUN, MON, TUE, WED, THU, FRI, SAT;
}
```

�������ͱȽϣ�Ҫʹ�� `equals()` ���������ʹ�� `==` �Ƚϣ����Ƚϵ��������������͵ı����Ƿ��� **ͬһ������** ����` enum` ���͵�ÿ�������� JVM ��ֻ��һ��Ψһʵ�������Կ���ֱ���� `==` �Ƚϡ�

### BigInteger

`java.math.BigInteger` ������ʾ�����С��������`BigInteger `�ڲ���һ�� `int[]` ������ģ��һ���ǳ�����������ǲ����࣬�̳��� `Number`��

### BigDecimal

��`BigInteger`���ƣ�`BigDecimal`���Ա�ʾһ�������С�Ҿ�����ȫ׼ȷ�ĸ�������

`scale()` �������Է���С��λ����

#### �ж����

`equals()`������Ҫ������ `BigDecimal` ��ֵ��ȣ���Ҫ�����ǵ� `scale()` ��ȣ�

`compareTo()`�������Ƽ����ַ����Ƚ� `BigDecimal` ��ֵ��

## �쳣����

### �쳣

Javaʹ���쳣����ʾ���󣬲�ͨ�� `try ... catch` �����쳣��

Java���쳣�� `class` �����Ҵ� `Throwable` �̳У�

`Error` �����貶������ش���`Exception `��Ӧ�ò���Ŀɴ���Ĵ���

`RuntimeException` ����ǿ�Ʋ��񣬷� `RuntimeException`��Checked Exception����ǿ�Ʋ��񣬻����� `throws` ������

### �����쳣

JVM�ڲ����쳣�󣬻ᰴ��ƥ��ĳ�� `catch` ��䲢ִ�У�Ȼ���ټ���ƥ�䣬����� `catch` ���ֻ��һ���ܱ�ִ�С�

#### finally ���

finally ��䣬���Ǳ���Ҫд�ġ�������֤һЩ�������ִ�У������Ƿ�׽���쳣��finally ��䶼�ᱻִ��

```java
public static void main(String[] args) {
    try {
        process1();
        process2();
        process3();
    } catch (UnsupportedEncodingException e) {//�����׽���쳣��ִ�ж�Ӧ�� catch ���
        System.out.println("Bad encoding");
    } catch (IOException e) {
        System.out.println("IO error");
    } finally {//�����Ƿ�׽���쳣��finally ��䶼�ᱻִ��
        System.out.println("END");
    }
}
```

### �׳��쳣

��ĳ�������׳����쳣ʱ�������ǰ����û�в����쳣���쳣�ͻᱻ�׵��ϲ���÷�����ֱ������ĳ�� `try ... catch` ������Ϊֹ����ʱ����ͨ�� `printStackTrace()` ���Դ�ӡ�������ĵ���ջ��

```java
public class Main {
    public static void main(String[] args) {
        try {
            process1();//���׵���һ����÷��� main() �У��쳣������
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    static void process1() {
        process2();//�׵���һ����÷��� process1() �У�����û�в�����쳣
    }

    static void process2() {
        Integer.parseInt(null); // process2()�� �׳�NumberFormatException��û�в�����쳣
    }
}

```

## Object ͨ�÷���

### �ȼ������

- ���ڻ������ͣ�== �ж�����ֵ�Ƿ���ȣ���������û�� equals() ������
- �����������ͣ�== �ж����������Ƿ�����ͬһ�����󣬶� equals() �ж����õĶ����Ƿ�ȼۡ�

### hashCode()

[hashcode() �� equals() �����ü�����](<https://blog.csdn.net/haobaworenle/article/details/53819838>)

- hashCode ��Ϊ�������ɢ�нṹ�洢�в��ҵ�Ч�ʣ������Ա���û�����ã�
- equals �� hashCode ��Ҫͬʱ���ǣ���֤�ȼ۵����������ɢ��ֵҲ���

### clone()

[clone() ������ʵ��](<https://www.jianshu.com/p/04ff0a7bf52b>)

####  **ǳ����** 

���������ԭʼ�����������������ͬһ������

####  **���** 

���������ԭʼ����������������ò�ͬ����

#### clone() ���������

ʹ�� clone() ����������һ�����󼴸������з��գ������׳��쳣�����һ���Ҫ����ת����Effective Java ���Ͻ�������ò�Ҫȥʹ�� clone()������ʹ�ÿ������캯�����߿�������������һ������

[ʾ��](<https://cyc2018.github.io/CS-Notes/#/notes/Java%20%E5%9F%BA%E7%A1%80?id=clone>)

## �ο�����

[CS-Notes](<https://cyc2018.github.io/CS-Notes/#/>)

[Java �̳�](<https://www.liaoxuefeng.com/wiki/1252599548343744>)
