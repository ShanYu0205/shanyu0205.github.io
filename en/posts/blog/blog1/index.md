# Java学习1


Java学习记录（一）
<!--more-->
# JAVA 学习

## 1.JAVA语言基础

### 1.1Java中的数值类型

### 1.1.1 数值类型

#### 1.1.2 数据类型转换

顾名思义，即为将一个值从一个类型转换为另一个类型的过程。例如，可以将String类型的数据“457”转换为数值型，也可以将任意类型的数据转换为String类型。<br/>

**如果从低精度数据类型向高精度数据类型转换，则永远不会溢出，即更加安全，并且总是成功，；而把高精度类型数据转换为低精度类型数据时，被可能存在数据的丢失，又可能失败**。

数据转换有两种形式，隐式转换（由低精度转换为高精度）与显式转换（由高精度转换为低精度）。<br/>

精度由低到高：（不包含逻辑类型与字符类型）<br/>
byte < short < int< long < float < double <br/>
例：

```java
int x =50;
float y = x; //由于浮点型精度高于整数型，所以此转换为隐式转换，结果为50.0
```

当我们需要把高精度的变量赋给低精度的变量时，必须使用显示类型转换运算（又称强制类型转换）。<br/>

例:

```java
int a = (int)45.23;     // 输出为45
long y = (long)456.5F;  // 输出为456
int b = (int)'d';       // 输出为100 
```

除布尔型以外，其他基本类型数据都能进行显型类型转换。

#### 1.1.3 运算符

在Java中有着算数运算符，关系运算符，位运算符，逻辑运算符，赋值运算符以及其他运算符。在此，我们主要讨论自增、自减运算符和位运算符。

```java
b = ++a;
b = a++;
```

上述两行代码看似差不多，实际上有很大区别：**第一行翻译为先将a的值+1，然后再赋给b；第二行则是先将a的值赋给b，a的值再+1。**

### 1.2类中的变量类型

- 局部变量：在方法，构造方法或者语句块中被定义的变量。方法结束后，变量会自动销毁。
- 成员变量：成员变量是定义在类中，方法体之外的变量，可以被类中方法、构造方法等语句块访问，**没有static修饰**。
- 类变量：类变量也申明在类中，方法体之外，**但必须声明为static类型**。

例：

``` java
public class Variable{
    static int allclicks = 0; // 类变量（静态变量）
    
    String str = "hello world"; // 实例变量（成员变量）

    public void method(){
        int i = 0; // 局部变量
    }
}
```

在Java中，所有变量在使用前都必须声明。<br/>
例：

```java
int a,b,c;          // 声明了3个int型整数：a，b，c。
int d = 3,e,f = 5;  // 声明三个整数并赋予初值。
byte z =22;         // 声明并初始化。
char x = 'x';       // 变量x的值是字符‘x’。
double pi = 3.14159;// 声明了pi。
```

既然有变量，那就会有常量。

### 1.3Java常量

常量就是一个固定值。他们不需要计算，直接代表相应的值。<br/>
常量指不能改变的值，在Java中用final标志：

```java
final double PI = 3.1415927;
```

### 1.4构造方法

每个类都有构造方法。

在创建一个对象时，至少要调用一个构造方法。构造方法的名称必须与类同名，**一个类可以有多个构造方法**。

例：

``` java
public class Puppy(){
    public Puppy(){

    }
    public Puppy(String name){

    }
}
```

上述代码类的构造方法为`Puppy()`,返回值为字符串类型的‘name’，即调用该构造方法时，`Puppy("name")`, 'name' 即为用户想输入的小狗的名字。

### 1.5创建对象

在Java中使用关键字 `new` 来创建一个新的对象。

- 声明：声明一个对象，包括对象名称和类型。
- 实例化：使用关键字 `new` 来创建一个对象。
- 初始化：使用 `new` 创建对象时，会调用构造方法(constructor)初始化对象。

例：

```java

public class Puppy(){
    public Puppy(String name){
        System.out.println("Puppy name is : "+ name);
    }
    public static void main(String []args){
        Puppy myPuppy = new Puppy("tommy");
        // 上述语句创建了一个Puppy对象
    }
}
```

代码块的结果会显示为：`Puppy name is tommy`

### 1.6访问实例变量和方法

``` java
/*实例化对象*/
ObjectReference = new Constructor();
/*访问其中的变量*/
ObjecReference.variableName;
/*访问类中的变量*/
bjecReference.MethodName();

public class Puppy(){
    int puppyAge; //定义了一个名为puppyAge的int型成员变量
    public Puppy(String name){
        System.out.println("Passed Name is: "+ name);
    }
    public void setAge(int age){
        puppyAge = age;
    }
    public int getAge(){
        System.out.println("Puppy's age is: " + puppyAge);
        return puppyAge;
    }

    public static void main(String []args){
        /*创建对象*/
        Puppy myPuppy = new Puppy("tommy");
        /*调用方法来设定age*/
        myPuppy.setAge(2);
        /*调用另一个方法来获取age*/
        myPuppy.getAge();
        /*访问成员变量*/
        System.out,println("Variable Value: " + myPuppy.puppyAge);
    }
}
```

结果为： <br/>
Passed name is: tommy  <br/>
Puppy's age is: 2 <br/>
Variable Value: 2

## 2.JAVA修饰符

- 访问修饰符
- 非访问修饰符<br/>
  
修饰符用来定义类、方法或者变量，通常放在语句的最前端。<br>
Java中，可以使用访问控制符来保护对类、变量、方法和构造方法的访问。Java 支持 4 种不同的访问权限。

- **default** (即默认，什么也不写）: 在同一包内可见，不使用任何修饰符。使用对象：类、接口、变量、方法。
- **private** : 在同一类内可见。使用对象：变量、方法。 **注意：不能修饰类（外部类)**
- **public** : 对所有类可见。使用对象：类、接口、变量、方法
- **protected** : 对同一包内的类和所有子类可见。使用对象：变量、方法。 **注意：不能修饰类（外部类）**。
  
### **默认访问修饰符-不使用任何关键字**<br>

使用默认访问修饰符声明的变量和方法，对同一个包内的类是可见的。接口里的变量都隐式声明为 `public static final`,而接口里的方法默认情况下访问权限为 `public`。

如下例，变量和方法的声明可以不适用任何修饰符：

```java
String version = "1.5.1"
boolean processOder(){
    return true
}
```

### **私有访问修饰符-private**<br>

私有访问修饰符是最严格的访问级别，所以被声明为`private` 的方法、变量和构造方法只能被**所属类访问**，并且类和接口不能声明为`private`。
声明为私有访问类型的变量只能通过类中公共的`getter` 方法被外部类访问。
**`Private` 访问修饰符的使用主要用来隐藏类的实现细节和保护类的数据。**
下面的类使用了私有访问修饰符`private`

```java
public class Logger {
   private String format;
   public String getFormat() {
      return this.format;
   }
   public void setFormat(String format) {
      this.format = format;
   }
}
```

`Logger` 类中的 `format` 变量为私有变量，所以其他类不能直接得到和设置该变量的值。为了使其他类能够操作该变量，定义了两个 `public`方法：`getFormat()` （返回 format的值）和 `setFormat`(String)（设置 format 的值）。

**公有访问修饰符-public**<br/>
被声明为 `public` 的类、方法、构造方法和接口能够被**任何其他类访问**。
如果几个相互访问的 `public` 类分布在不同的包中，则需要导入相应 `public`类所在的包。由于类的继承性，类所有的公有方法和变量都能被其子类继承。最常见的公有访问即为`public static void main(String []args){...}`。Java 程序的`main()`方法必须设置成公有的，否则Java 解释器将不能运行该类。

### **受保护的访问修饰符-protected**<br/>

被声明为`protected`的变量、方法和构造器能被同一个包中的任何其他类访问，也能被不同包中的字类访问。<br>

## 非访问修饰符

- 例如`static`修饰符，用来创建方法和类变量。
- `final`修饰符，用来修饰类、方法和变量，`final`修饰的类不能被继承，修饰的方法不能被继承重新定义，修饰的变量是不可修改的。
- `abstract`修饰符，用来创建抽象类和抽象方法。
-`synchronized`和`volatie`修饰符，主要用于线程的编程。

### **`final`修饰符(关键字)**<br>

`final`变量能被显式地初始化并且只能初始化一次。被声明为`final`的对象的引用不能指向不同对象。但是final对象里的数据可以被改变，也就是说`final`对象的引用不能改变，但是里面的值可以改变。<br>
`final`修饰符通常和`static`修饰符一起是用来创建常量。<br>
例：

```java
public class Test{
    final int value = 10;
    //  下面是声明常量的实例
    public static final int BOXWIDTH = 6;
    static final String TITLE = "Manager";

    public void changeValue(){
        value = 12;//将输出一个错误
    }
}
```

由于value的值已经被final定义过，所以无法被改变。<br>

类中的`final`方法可以被字类继承，但是不能被字类修改。`fianl`类不能被继承，没有类能够继承`final`类的任何特性。

### static修饰符

- 静态变量：<br>
  static关键字用来声明独立于对象的静态变量，静态变量也被称为类变量。局部变量不能被声明为static变量。<br>

例：

```java
public class InstanceCounter{
    private static int numInstances = 0;
    protected static int getCount(){
        return numInstances;
    }

    private static void addInstance(){
         numInstances++;
    }

    InstanceCounter(){
        InstanceCounter.addInstance();
    }

    public static void main(String []args){
        System.out.println("Starting with "+:InstanceCounter.getCount()+ "instances");
        for (int i = 0; i < 500; i++){
            new InstanceCounter();
        }
        System.out.println("Created "+ InstanceCounter.getCount()+" instances");
    }
}
```

结果如下：<br>

```java
Started with 0 instances
Created 500 instances
```

