### ArrayList 

数组的长度不可以发生改变，但是ArrayList集合的长度是可以随意变化的。

对于ArrayList来说，有一个尖括号<E>代表泛型

泛型：也就是装在集合当中的所有元素，全都是统一的某种类型。

注意：泛型只能是引用类型，不能是基本类型

```java
ArrayList<String> list = new ArrayList<>(); 
备注：从JDK 1.7+ 开始,右侧的尖括号内容可以不写内容，但是<>本身还是要写的。
  
ArrayList当中的常用方法有：
public boolean add(E e) : 向集合当中添加元素，参数的类型和泛型一致。返回值代表添加是否成功。
备注：对于ArrayList集合来说，add添加动作一定是成功的，所以返回值可用可不用。但是对于其他集合来说，add添加动作不一定成功。
 // 向集合中添加元素： add
        boolean success = list.add("一辈子");
        System.out.println("添加动作是否成功：" + success);
        System.out.println(list);
 
public E get(int index): 从集合当中获取元素，参数是索引编号，返回值就是对应位置的元素。
  // 从集合中获取元素
        String s = list.get(0);
        System.out.println(s);
public E remove(int index): 从集合当中删除元素，参数是索引编号，返回值就是被删除掉的元素。
 // 从集合中删除元素
        String removed = list.remove(2);
        System.out.println(list);
public int size(): 获取集合的尺寸长度，返回值是集合中包含的元素个数。
// 获取集合的长度 
    	int size = list.size();
        System.out.println(size);



如果希望向集合ArrayList当中存储基本类型数据，必须使用基本类型对应的"包装类”
基本类型  包装类（引用类型 包装类都位于java.lang包下）
byte     Byte
short    Short
int      Integer
long     Long
float    Float
double   Double
char     Character
boolean  Boolean
  
自动装箱： 基本类型 -> 包装类型
自动拆箱:  引用类型 -> 基本类型
```

### String类

java.lang.String类代表字符串

`String` 类代表字符串。Java 程序中的所有字符串字面值（如 `"abc"` 
）都作为此类的实例实现。 也就是说，程序当中所有的双引号字符串都是`String类` 的对象，就算没有new，也照样是 。

**字符串的特点**  

1. 字符串的内容永不可变。`重点` 
2. 正是因为字符串不可改变，所以字符串是可以共享使用的。
3. 字符串效果上相当于是char[ ]字符数组，但是底层原理是byte[ ]字节数组

```java
创建字符串的常见3+1中方式：  

3种构造方法： 

public String() : 创建一个空白字符串，不含有任何内容
  //使用空参构造
  String str1 = new String();     //小括号留空，说明字符串什么内容也没有
  System.out.println("第一个字符串:" + str1);

public String(char[] array): 根据字符数组的内容，来创建对应的字符串
  //根据字符数组创建字符串
  char[] charArray = {'A', 'B', 'C'};
  String str2 = new String(charArray);     
  System.out.println("第二个字符串:" + str2);

public String(byte[] array): 根据字节数组的内容，来创建对应的字符串
   byte[] byteArray = {97, 98, 99};
   String str3 = new String(byteArray);
   System.out.println("第三个字符串:" + str3);


1种直接创建
String str4 = "hello";

```

字符串常量池：程序当中直接写上的双引号字符串，就在字符串常量池中。

对于基本类型来说，`==` 是进行数值的比较

对于引用类型来说，`==`是进行地址值的比较

![String](https://github.com/daohewang/JavaLearningNote/blob/master/noteImg/Java/String.png?raw=true)



== 是进行对象的地址值的比较，如果确实需要字符串的内容比较，可以使用两个方法：

```java
字符串的内容比较：

public boolean equals(Object obj) : 参数可以是任何对象，只有参数是一个字符串并且内容相同的才会是true；否则返回false
  注意事项：
  	1. 任何对象都能用Object进行接收
  	2. equals方法具有对称性，也就是a.equals(b)和b.equals(a)效果一样。
  	3. 如果比较双方一个常量一个变量，推荐把常量字符串写在前面 
  	   推荐："abc".equals(str)     不推荐：str.equals("abc")
  
public boolean equalsIgnoreCase(Object obj) : 不区分大小写比较
```

```java
String 当中与获取相关的常用方法有：
  public int length(): 获取字符串当中含有的字符个数，拿到字符串长度。
  public String concat(String str): 将当前字符串和参数字符串拼接成为返回值新的字符串
  public char charAt(int index): 获取指定索引位置的单个字符
  public int indexOf(String str): 查找参数字符串在本字符串当中首次出现的索引位置，如果没有返回-1
  
```

```java
字符串的截取方法：
 
public String substring(int index):  截取从参数位置一直到字符串结尾，返回新字符串
  
public String substring(int begin, int end): 截取从begin开始，一直到end结束，中间的字符串
备注：[begin, end),包含左边，不包含右边。
    
注意：下面这种写法，字符串的内容仍然是没有改变的，下面的两个字符串："Hello" , "Java". strA当中保存的是地址值。本来地址值是Hello的0X666，后来地址值变成了Java的0x999;  
    String strA = "Hello";
    System.out.println(StrA);    //Hello
    strA = "Java";
    system.out.println(strA);   //Java
   
```

```java
String当中与转换相关的常用方法：
  public char[] toCharArray(): 将当前字符串拆分成为字符数组作为返回值
  public byte[] getBytes(): 获得当前字符串底层的字节数组
  public String replace(CharSequence oldString, CharSequence newString): 将所有出现的老字符串替换成为新的字符串，返回替换之后的结果新字符串。
```

```java
分割字符串的方法： 
  public String[] split(String regex):  按照参数规则，将字符串切分成为若干部分
  注意事项：如果按照英文句点"." 来切分的话，需要使用 "\\."来使用。因为英文句点在正则表达式中有特殊含义。
```

### static关键字

![static图解](https://github.com/daohewang/JavaLearningNote/blob/master/noteImg/Java/static.png?raw=true)  

- 如果一个成员变量使用了static关键字，那么这个变量不再属于对象自己，而是属于所在的类。多个对象共享同一份数据。
- 一旦使用static修饰成员方法 ，那么这就成为了静态方法。静态方法不属于对象单独所有，而属于类 
- 如果没有static关键字，那么必须首先创建对象，然后再通过对象调用其方法。 
- 对于静态方法来说，可以直接使用类名称来直接调用(推荐)。
- 总结：无论是成员变量还是成员方法，如果有了static，都推荐使用类名称来进行调用
  - 静态变量： 类名称.静态变量
  - 静态方法:   类名称.静态方法();
- 备注：对于自己类中的静态方法，调用时类名称可以省略。
- 注意：
  1. 静态不能直接访问非静态。原因是因为内存当中是先有静态内容，然后再有非静态内容 (古人不知道后人，后人知道古人)。
  2. 静态方法当中不能用this关键字。原因是因为this代表对象，通过谁调用的方法，谁就是对象。  
- **静态static内存图**

![staticValue](..\noteImg\Java\staticValue.png)

- **静态代码块**

```java
格式： 
  public class 类名称 {
    static {
      //静态代码块内容
    }
  }
特点：当第一次用到本类时，静态代码块执行唯一的一次
  	  静态内容总是优先于非静态，所以静态代码块比构造方法先执行。
典型用途： 用来一次性地对静态成员变量进行赋值
```



### 数组工具类Arrays  

java.util.Arrays是一个与**数组相关**的工具类，里面提供了大量的静态方法，用来实现数组的常见操作。

```java
public static String toString(数组) ： 将参数数组变成字符串(按照默认格式)
public static void sort(数组): 按照默认升序(从小到大)对数组元素进行排序
 备注：
  	1.如果是数值，sort默认按照升序从小到大。
  	2.如果是字符串，sort默认按照字母升序
   	3.如果是自定义类型，那么这个自定义的类需要有Comparable或者Comparator接口支持。
```
### 常用Math类

```java
java.util.Math类是数学相关的工具类，里面提供了大量的静态方法，完成与数学运算相关的操作

public static double abs(double num): 获取绝对值。
public static double ceil(double num): 向上取整
public static double floor(double num): 向下取整
public static long round(double num): 四舍五入
```
### 接口的使用：

**定义：** 接口就是多个类的公共规范，它属于一种引用类型，最重要的内容是其中的`抽象方法`  。

**接口定义格式：**  

```java
public interface 接口名称 {
  // 接口内容
}
备注：换成了关键字interface之后，编译生成的字节码文件仍然是：.java -> .class
// 如果是java 7，那么接口可以包含的内容有： 
  1. 常量
  2. 抽象方法
  注：抽象方法定义格式：public abstract void methodAbs();
 // 如果是Java 8, 还可以额外包含有：
  3. 默认方法
  4. 静态方法
  // 如果是Java 9，还可以额外包含有：
  5. 私有方法
```

在任何版本的Java中，接口都能定义抽象方法。

```java
格式： public abstract 返回值类型 方法名称(参数列表);
```

**注意事项：**

1. 接口当中的抽象方法，修饰符必须是两个关键字：public abstract。(也可以省略其一或全不写)
2. 方法的3要素，可以随意定义。

**接口使用步骤：** 实现类 -> 创建实现类对象  

1. 接口不能直接使用，必须有一个`实现类` 来 `实现` 该接口。

   格式：public class 实现类名称 implements 接口名称 {

   ​	// .....

   }  

   2. 接口的实现类必须覆盖重写(即实现)接口中所有抽象方法。

   实现：去掉abstract关键字，加上方法体大括号 

   3.  创建实现类的对象，进行使用。

   **注意事项：**如果实现类并没有覆盖重写接口中所有的抽象方法,那么这个实现类自己就必须是抽象类。

**从Java 8开始，接口里允许定义默认方法。**

```java
格式：
public default 返回值类型 方法名称(参数列表) {	

	方法体

}
备注：接口当中的默认方法，可以解决接口的升级问题。
```

1. 接口的默认方法，可以通过接口实现类对象，直接调用。

2. 接口的默认方法，也可以被接口实现类进行覆盖重写。

   备注：调用抽象类方法，实际上运行的是右侧实现类。  



**从Java 8开始，接口里允许定义静态方法。**  

```java
格式：
public static 返回值类型 方法名称(参数列表){
  // 方法体
}
注意事项：不能通过接口实现类的对象来调用接口当中的静态方法。
正确用法：通过接口名称，直接调用其中的静态方法
  格式：接口名称.静态方法名(参数);	
```
**从Java 9开始，接口里允许定义私有方法。**  

```java
1. 普通私有方法，解决多个默认方法之间代码重复问题。
格式 ：
private 返回值类型 方法名称(参数列表) {
	方法体 
}
2. 静态私有方法，解决多个静态方法之间重复代码问题
格式：
private static 返回值类型 方法名称(参数列表){
  方法体 
 }
```

**接口常量：**

接口当中也可以定义 “成员变量” ，但是必须使用public static final 三个关键字修饰。从效果看，这其实就是接口的`常量` 

```java
格式：
public static final 数据类型 常量名称 = 数据值;

备注: 一旦使用final关键字进行修饰，说明不可改变。
注意事项：
  1. 接口当中的常量，可以省略public static final，注意：不写也照样是原本的样子
  2. 接口当中的常量，必须进行赋值；不能不赋值
  3. 接口中常量的名称，使用完全大写的字母，用下划线进行分隔(推荐命名规则)
```

**使用接口时，需要注意的事项：**  

```java
1. 接口是没有静态代码块或者构造方法的。
2. 一个类的直接父类是唯一的,但是一个类可以同时实现多个接口。
格式：public class MyInterfaceImpl implements MyInterfaceA, MyInterfaceB {	
   	// 覆盖重写所有抽象方法
   }
3. 如果实现类所实现的多个接口当中，存在重复的抽象方法 ，那么只需要覆盖重写一次即可。
4. 如果实现类没有覆盖重写所有接口当中的抽象方法，那么实现类就必须是一个抽象类。
5. 如果实现类所实现的多个接口当中，存在重复的默认方法，那么实现类一定要对冲突的默认方法进行覆盖重写。
6. 一个类如果直接父类当中的方法，和接口当中的默认方法产生了冲突，优先使用父类当中的方法。

```