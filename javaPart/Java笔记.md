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
- 一旦使用static修饰成员方法 ，那么这就成为了静态方法。静态方法不属于对对象，而属于类 