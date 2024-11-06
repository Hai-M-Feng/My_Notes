# JAVA基础

## 前言

这个东西算是我学习 Java 的笔记，所以没有包含编程的基础概念，适合学完 C++/C 的人阅读，帮助快速过渡到 Java

## 第一个程序

### 编写部分

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.print("Hello World");
    }
}
```

`public class` 公共的类

`public static void main(String[] args)` 主函数

`System.out.print("Hello World")` Java中的输出方法

### 生成文件

在 `.java` 文件所在的目录打开 cmd

输入 `javac <文件名>.java` 

确认生成了 `.class` 文件

cmd 输入 `java <类名>` 运行(不带 `.class`)

> 之后会使用 IDEA，这个了解就行

### 注释

和 c++ 一样，可以使用 `// ...` 或者 `/* ... */` 进行注释

可以使用文档注释，`/** ... */`

---

## 变量

### 数据类型

两种，分为 基本数据类型 和 引用数据类型

基本数据类型有：

* 整数
  
  * `byte` 1字节 $-2^{7} \sim 2^{7}-1$ 或 $-128 \sim 127$ 
  
  * `short` 2字节 $-2^{15} \sim 2^{15}-1$ 或 $-32768 \sim 32767$
  
  * `int` 4字节 $-2^{31} \sim 2^{31}-1$ 或 $-2147483648 \sim 2147483647$
  
  * `long` 8字节 $-2^{63} \sim 2^{63}-1 $ 约 19位数 后面要加"L"

* 小数
  
  * `float` 4字节
  
  * `double` 8字节，实际上 `double` 范围远比 `long` 大
  
  * **注意：`double` 为默认浮点类型，`float` 在赋值时需要在后面额外加个“F”**

* 布尔
  
  * `boolean` 大小没有明确规范，但编译器通常会优化存储 `true/false` 

* 字符
  
  * `char` 2字节 $0 \sim 65535$ 使用 Unicode编码
  
  * 常用转义字符 `'\n', '\t', '\\', '\'', '\"'`

引用数据类型（不是基本数据类型的都是）有：

* 字符串
  
  * `String` Unicode字符序列

* 数组

* 对象

* etc

### 声明变量

```java
<关键字> <变量名> = <初始值>;
```

和 c++ 区别不大

数组的声明有区别，后面再写

---

## 运算符

### 算术运算符

单目 `++ --`

双目 `+ - * / = % += -= *= /= %=`

### 关系运算符

双目 `> < >= <= == !=`

### 逻辑运算符

单目 `!`

双目 `&& ||`

三目 `? :`

---

## 输入输出

### 导入 Scanner 类

在主类之前导入 `java.util.Scanner` 类

```java
import java.util.Scanner;
```

### 创建一个 Scanner 对象

在主函数里面创建一个 `Scanner` 对象

```java
Scanner myscanner = new Scanner(System.in);
```

### 调用 Scanner 输入

`myscanner.nextInt()` 可以读取并返回一个整数（这里使用的是你创建的对象）

以此类推，还有 `nextDouble()` 等，注意 `next()` 是读取一个字符串

因为 Java 没有直接读入字符的方法，可以使用 `next().charAt(0)` ，这里是返回字符串的第一个字符

可以直接使用赋值的方法 `int n = myscanner.nextInt();`

### 输出

`System.out.println();` 可以直接输出，使用加号可以连接多个字符串

`System.out.printf();` 使用格式控制符，类似于 `scanf` 

 ---

## 分支结构

### if 结构

```java
if (<布尔表达式>) {
    //代码（这不就是 C 吗）
}
```

### if-else 结构

```java
if (<布尔表达式>) {
    //代码（这不就是 C 吗）
}
else {
    //代码（这不还是 C 吗）
}
```

这俩都可以连续使用，可以嵌套

### switch 结构

```java
switch (<变量或表达式>) {
    case <值1>:
        //代码
        //break;
    case <值2>:
        //...
    default:
        //还是 C
}
```

---

## 循环结构

### while 结构

```java
while (<布尔表达式>) {
    //c++ 还在追我
}
```

### do...while 结构

```java
do {
    //....
} while (<布尔表达式>)
```

### for 结构

```java
for (<初始语句>; <循环条件>; <迭代部分>) {
    //代码
}
```

**`break` 和 `continue` 也可以使用**

循环可嵌套

### 增强的 for 结构

```java
int[] a = {1, 2, 3, 4};
int sum = 0;
for (int j : a) { //表示遍历 a 中的每个元素，分别用 j 存储
    sum += j;
}
```

---

## 方法

面向过程时一般把方法叫做函数（C）

面向对象时叫做方法（Java）

这俩实际上是一个东西

### 定义一个方法

```java
public static void <方法名称>() {
    //代码
}
```

### 传参

```java
public static void <方法名称>(<形式参数1>, <形式参数2>, ...) {
    //代码
}

//调用
<方法名称>(<实际参数1>, <实际参数2>, ...);
```

### 返回值

```java
public static <方法类型> <函数名称>() {
    return <对应类型的返回值>;
}
```

方法里面不能定义方法

---

## 数组

### 数组的声明

```java
int[] a = new int[n];
<数据类型>[] <数组名称> = new <数据类型>[<数组长度 接受变量(整型)>];
//也可以分开声明和定义
//还能在声明的时候直接初始化
int[] a = {1, 2, 3, 4, 5};
```

**使用 `new` 初始化数组时，各类型的初始值：**

* `int` `0`

* `double / float` `0.0`

* `boolean` `false`

* `char` `\u0000` (ASCII码的第一个位置)

* `string` `Null`

### 数组的调用

```java
System.out.println(a[1]);
a[1] = 5;
a[2] = a[1];
a[0] = myscanner.nextInt();
```

**小技巧：`<数组名>.length` 可以直接获取数组长度，比如 `a.length`**

### 数组的传参

引用数组

```java
//引用调用
public static void main(String[] args) {
    int[] a = new int[10];
    print(a);//这里传的是数组名（实际上代表的就是这个数组的地址）
}
//这里实际上就是把数组 a 的地址给了 b，对 b 操作仍然会改变 a 的值
public static void print(int[] b) {
    for (int i = 0; i < b.length; b++)
        System.out.println(b[i]);
}
```

返回数组

```java
public static void main(String[] args) {
    int[] a;
    a = setNums(100);
}
//这里定义了一个整型数组类型的方法
public static int[] setNums(int n) {
    int[] b = new int[n];
    return b;//返回的也是数组的地址
}
```

可变参数

```java
public static void main(String[] args) {
    System.out.println(add());
}

public static int add(int... nums) {
    int sum = 0;
    for (int i = 0; i < nums.length; i++)//这里直接把nums当作数组使用
        sum += nums[i];
    return sum;
}
```

### 二(多)维数组

```java
int[][] a = new int[100][20];
int[][][] b = new int[c][d][e];
//调用方式和c++一样
```

---

## 类与对象

### 基本概念

**类**

把找出一类物体的相同特征，并抽象为一个整体就是 类

比如我们有相同的特征：

* 都要去上课

* 都要吃饭

* 都要睡觉

* 年龄差距不大

* 都是人

那我们可以抽象为一个 学生类

**对象**

一个类的具体的实例就是一个对象

按照上面的例子，你我都是 学生类 里面的一个对象

**类的继承**

对与归属于某些父类的子类，我们可以让子类继承父类的特性

比如我们都是 人类，人类 中可以细分出 学生类，学生类 包含 人类 的全部特征

### 类

**创建一个 `Human` 类**

一个类里面可以包含变量，方法

```java
public class Human {
    private String name;//别人没法直接得到你的名字，所以是private（私有）类型
    private int age;//同理
    public double height;//别人能直接看出你的身高，所以算是public（公开）类型

    public String getName() {//别人问你名字，你总得回答吧
        return name;//所以可以通过这个公开方法获得你的名字
    }
    protected int getAge() {//别人问你年龄，你不一定要告诉他，算是protected（保护）
        return age;//所以熟悉的人（子类或者同包的类）可以问你
    }
}
```

上面出现了三种权限修饰符：

* `public` 公开，可以被外部直接访问，一般不用于变量，常用于方法

* `protected` 保护，只有该类，子类，同包的类可以访问

* `private` 私有，只有该类可以访问

通过这三种权限修饰符，可以保证用户只能通过给定的方法访问这个类，提高了安全性

### this 关键字

`this` 用于表示该类当前的对象，`this` 只能在本类中使用

```java
public class Human {
    private String name;//这是一个私有的变量
    //但是我们可以通过一个公开的方法对这个变量赋值
    public void setName(String temp) {
        this.name = temp;//this 表示当前对象
    }
}
```

你甚至可以直接使用 `this` 调用本对象，但是要注意返回的实际上是该对象的引用

```java
public static void main(String[] args) {
    Human me = new Human();//这里创建了两个对象，分别是 me 和 copyMe
    Human copyMe = new Human();
    me.setName("HaiMFeng");//调用 setName 方法修改 me 的属性
    copyMe = me.copyHuman();//调用 copyHuman 方法把 me 赋给 copyMe
    System.out.println(copyMe.getName());
}

public static class Human {
    private String name;
    public void setName(String temp) {
        this.name = temp;
    }
    public String getName() {
        return this.name;
    }
    public Human copyHuman() {//这里直接返回了该对象
        //return this;这样写是不好的，因为实际上是返回了该对象的引用
        Human temp = new Human();
        temp.name = this.name;
        return temp;
    }
}
```

### 类的构造方法

Java 中的构造方法比 C++ 简单多了

```java
public static void main(String[] args) {
    Human me = new Human("HaiMFeng");//调用构造方法初始化
    System.out.println(me.getName());
}

public static class Human {
    private String name;
    //构造方法
    public Human(String temp) {//有字符串输入时的构造方法
        this.name = temp;
    }
    public Human() {//没有输入时的默认构造
        //注意在调用自身的构造方法时 this 必须在第一句
        this("");//调用了上面的含参构造方法，传入默认值
    }
    public String getName() {
        return this.name;
    }
}
```

### Static 关键字

由 `static` 关键字修饰的方法和变量，被称为静态方法和静态变量

静态变量的例子：

```java
public static void main(String[] args) {
    System.out.println(Nothing.PI);//可以直接使用类名调用，而不用使用对象名
}

public static class Nothing {
    public static double PI = 3.1415926535;//这个就是静态变量
}
```

静态方法的例子

```java
public static void main(String[] args) {
    //可以直接使用类名调用方法，而不用使用对象名
    System.out.println(Calculator.add(1, 5));

    //这样写是错误的，subtract 不是静态方法，需要先实例化 Calculator 类才能调用
    //System.out.println(Calculator.subtract(1, 5));

    //正确的方式：先实例化 Calculator 类，然后调用 subtract 方法
    //这种方式比调用静态方法麻烦多了
    Calculator calc = new Calculator();
    System.out.println(calc.subtract(1, 5)); // 输出: -4
}

public static class Calculator {
    public static int add(int num_1, int num_2) {//add 是静态方法
        return num_1 + num_2;
    }
    public int subtract(int num_1, int num_2) {//subtract 是普通方法
        return num_1 - num_2;
    }
}
```

### 类的主方法

之前应该都见过了

```java
public static void main(String[] args) {...}//反正这么写就对了
```

~~主方法必须是公开的~~（废话）

主方法必须是静态的，这是为了让 `JVM` 能找到静态接入点

主方法是没有返回值的

主方法必须接受一个 `String` 类型的数组，`JVM` 只会从有这个标识的 `main` 方法进入

> 你可以直接当作 C/C++ 的 main 函数

### 创建对象

之前也见的差不多了

```java
<类名> <对象名> = new <类名>(<初始值（如果有的话）>);
```

就是这样

### 访问对象

之前也见了不少了

```java
//访问对象中的属性
<对象名> . <变量名>
//调用对象中的方法
<对象名> . <方法名> (<参数（如果有的话）>);
```

### 对象的引用

**这个是重点**，之前学 `this` 的时候写了这么个程序

```java
public static void main(String[] args) {
    Human me = new Human();//这里创建了两个对象，分别是 me 和 copyMe
    Human copyMe = new Human();
    me.setName("HaiMFeng");//调用 setName 方法修改 me 的属性
    copyMe = me.copyHuman();//调用 copyHuman 方法把 me 赋给 copyMe
    System.out.println(copyMe.getName());
}

public static class Human {
    private String name;
    public void setName(String temp) {
        this.name = temp;
    }
    public String getName() {
        return this.name;
    }
    public Human copyHuman() {//这里直接返回了该对象
        //return this;这样写是不好的，因为实际上是返回了该对象的引用
        Human temp = new Human();
        temp.name = this.name;
        return temp;
    }
}
```

为什么这里说 `return this;` 是不对的呢？

首先，这里的 `me copyMe` 或者是 `this`

它们实际上都是对象的引用（可以理解为这个对象所在的地址）

在 `Human me = new Human();` 中，`me` 是引用，`new Human()` 实际上是创建了一个实例，然后把这个实例的引用赋值给了 `me` 这个操作标识符

再看上面的程序，如果直接 `return this;` ，返回的实际上是 `me` 的引用，这就让 `copyMe = me.copyHuman();` 是把 `me` 的引用赋值给了 `copyMe` ，这个时候再调用 `copyMe` 的话，实际上是访问了 `me` 的实例

> 你可以理解为 c++ 中这俩指针指向了同一个内存地址
> 
> 虽然 `me` 和 `copyMe` 在 Java 中实际上并不是指针

### 对象的销毁

首先，Java 有一套完整的垃圾回收机制，对使用完的对象会自动清理其内存地址

```java
public static void main(String[] args) {
    Human me = new Human();
    //.....
    //你的程序结束了
}// <- JVM 会在这里回收 me 的内存，即 me 的作用域结束的地方
```

其次，你还可以手动销毁对象

```java
public static void main(String[] args) {
    Human me = new Human();
    //.....
    me = null;// <- JVM 会在这里回收 me 的内存
    //你的程序结束了
}
```

---

## 继承、多态、抽象类与接口

### 类的继承

继承，就是让子类保留父类除了私有以外的所有属性以及行为，并且加以扩充

```java
class <子类名> extends <父类名> {...}
```

使用上面的语句可以创建一个继承于父类的子类

**一个子类只能有一个父类，一个父类能有多个子类**

比如之前写的 `Human` 类，我们可以创建一个 `Student` 类 继承 `Human` 类的特性

> 虽然子类不能直接访问父类中 `private` 的属性，但是仍然可以通过公开方法调用

```java
public static class Human {
    private String name;//别人没法直接得到你的名字，所以是private（私有）类型
    private int age;//同理
    public double height;//别人能直接看出你的身高，所以算是public（公开）类型

    public String getName() {//别人问你名字，你总得回答吧
        return name;//所以可以通过这个公开方法获得你的名字
    }
    protected int getAge() {//别人问你年龄，你不一定要告诉他，算是protected（保护）
        return age;//所以熟悉的人（子类或者同包的类）可以问你
    }
}
//创建一个 Student类 继承自 Human类
public static class Student extends Human {
    private String university;//这里声明了两个 Human类 没有的变量
    private int grade;
    public String getUniversity() {
        return university;
    }
    public int getGrade() {
        return grade;
    }
}

public static void main(String[] args) {
    Student me = new Student();
    System.out.println(me.getUniversity());//这个是 Student类 里面的
    System.out.println(me.getAge());//这个是继承自父类的，但是子类可以直接调用
}
```

### 子类的构造

在构造子类时，我们可以通过 `super` 关键字来调用父类的构造方法

```java
public static class Human {
    private String name;
    private int age;
    public double height;

    public String getName() {
        return name;
    }
    protected int getAge() {
        return age;
    }
    public Human() {//父类的默认构造方法
        this("", 0);
    }
    public Human(String sName, int iAge) {//父类的构造方法
        this.name = sName;
        this.age = iAge;
    }
}
//创建一个 Student类 继承自 Human类
public static class Student extends Human {
    private String university;
    private int grade;
    public String getUniversity() {
        return university;
    }
    public int getGrade() {
        return grade;
    }
    public Student() {//子类的默认构造方法
        this("", 0, "", 0);
    }
    public Student(String sName, int iAge, String sUniversity, int iGrade) {
        super(sName, iAge);//子类的构造方法
        this.university = sUniversity;
        this.grade = iGrade;
    }
}

public static void main(String[] args) {
    Student me = new Student("HaiMFeng", 18, "HFUT", 1);
    System.out.println(me.getUniversity());//这个是子类构造的
    System.out.println(me.getAge());//这个使用父类的构造方法出来的
}
```

### Object 类

`java.lang.Object` 类是所有类的父类

Java 中的所有类都继承自 `Object` （包括自定义类）

`Object` 类提供了许多好用的方法

#### getClass() 方法

`getClass` 能够返回该对象的类

```java
public static void main(String[] args) {
    Human me = new Human();
    System.out.println(me.getClass());//调用 getClass 方法，返回类
}

public static class Human {
    String name;
}
```

> 这段输出的是 `class Example$Human` 
> 
> 表示 `me` 属于 `Example` 类（运行这段代码时的主类）中的 `Human` 类

#### toString() 方法

可以把对象以字符串的形式返回

```java
public static void main(String[] args) {
    Human me = new Human();
    System.out.println(me);//调用默认的 toString 方法
}
public static class Human {
    String name;
}
```

> 返回的是 `Example$Human@b4c966a` ，这是虚拟机看到的类的信息
> 这样显然不便于使用，所以我们通常在自定义类中重写 `toString()` 方法

```java
public static void main(String[] args) {
    Human me = new Human();
    System.out.println(me);//默认调用重写的 toString 方法
}
public static class Human {
    String name = "HaiMFeng";

    @Override//用来标注这是重写的方法
    public String toString() {//这里重写了 toString 方法
        return name;
    }
}
```

> 返回的是 `HaiMFeng` ，即我们重写的 `toString` 方法的行为
> **由此我们可以看出，子类可以重写父类的方法**

#### equals() 方法

我们可以在自定义类中来重写 `equals` 方法，来满足我们比较的需求

```java
public class Human {
    private String name;

    public Human() {
        this.name = ""; // 默认构造函数设置默认姓名
    }

    public Human(String name) {
        this.name = name; // 带参数的构造函数
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true; // 如果是同一个对象，直接返回true
        if (obj == null || getClass() != obj.getClass()) return false;
        // 如果传入的对象为空或不是同一个类型，返回false
        Human human = (Human) obj; // 将传入的对象转换为Human类型
        return name.equals(human.name); // 比较两个对象的名字是否相同
    }

    @Override
    public int hashCode() {
        return name != null ? name.hashCode() : 0; 
        // 如果name不为空，则返回name的hashCode值；否则返回0
    }
}
```

重写了以后，可以直接使用 `equals` 方法来比较两个对象是否相等

### 对象类型的转换

#### 向上转型

可以理解为将子类类型的对象转换为父类类型的对象，例如：

```java
Human me = new Student();//子类 Human 是 Student 的父类
```

这里说明了有个 `Human` 类的 `me` 是个 `Student`

> 向上转型时，父类的对象无法调用子类的属性和方法

#### 向下转型

可以理解为将父类类型的对象转换为子类类型的对象

通常来说，向下转型是不安全的

```java
Human me = new Student();//我们可以说某个学生是人类（废话）
Student student = me;//但是我们不能这么写，因为人不一定是学生
```

因此，我们需要告诉 `JVM` ，这个人就是一个学生（强制转换）

```java
Human me = new Student();//我们可以说某个学生是人类（废话）
Student student = (Student) me;//告诉 JVM 这个人就是学生
```

> 注意：向下转型之前，父类的对象必须先引用过子类
> 
> 如果没有引用就会报错，比如
> 
> ```java
> Human me = new Human();//这里使用了 Human类 的构造方法
> Student student = (Student) me;//这样写是错误的，会报错
> ```
> 
> 没有继承关系的类不能转型

### instanceof 关键字

在向下转型之前，应该先判断父类对象是否是子类对象的实例

这里可以使用 `instanceof` 关键字：

```java
myobject instanceof ExampleClass
```

这里判断某个类的对象的引用是否是 `ExamlpeClass` 的对象

如果是，返回 `true` 否则返回 `false`

**注意这个关键字只能判断有继承关系的类与对象**

例子：这里定义了几个类，并判断它们对象的关系

```java
public static class Human { }
public static class Student extends Human { }
public static class Cat { }

public static void main(String[] args) {
    Human man = new Human();
    Student studentA = new Student();
    Cat catA = new Cat();
    System.out.println(man instanceof Student);
    System.out.println(studentA instanceof Human);
    //System.out.println(catA instanceof Student);
    //不能这么写，Cat与Student没有继承关系
}
```

> 运行结果是
> 
> ```java
> false
> true
> ```
> 
> 这是因为 `man` 不是 `Student` 类的子类的对象
> 
> 而 `studentA` 是 `Human` 类的子类的对象

### 方法的重载

为了匹配多样的需求，可以在同一个类里面包含多个同名方法，只要它们的参数类型或者参数个数不同即可

这里使用多个 `add` 方法来举例

```java
public static int add(int a, int b) {
    return a + b;
}

public static double add(double a, double b) {
    return a + b;
}

public static int add(int a) {
    return a;
}

public static int add() {
    return 0;
}

public static int add(int... a) {
    int sum = 0;
    for (int i = 0; i < a.length; i++) {
        sum += a[i];
    }
    return sum;
}
```

> 你可以在主方法里面调用 `add` 方法，只要传入的参数不同，返回的值也不同

### final 关键字

`final` 关键字修饰的变量，方法，类有特殊的性质

* `final` 修饰的变量不能被修改

```java
final double PI = 3.1415926;
//final 修饰PI 的值不能被修改
```

> 如果尝试修改一个 `final` 变量的值，编译器会报错

* `final` 修饰的方法不能被重写

```java
public class Human {
    protected String name;
    public final void setName(String namet) {
        this.name = namet;
    }
}

public class Student extends Human {
    @Override
    public void setName(String namet) {
        this.name = namet;
    }
}
```

> 上面这种写法会报错，因为尝试重写一个 `final` 方法

* `final` 修饰的类不能被继承

```java
public static final Test() {
    public static int add(int a, int b) {
        return a + b;
    }
}

public class Test1 extends Test {
    //.....
}
```

> 上面这种写法会报错，因为尝试继承一个 `final` 类
> 
> Java 中有些类也是 `final` 类，比如说 `Math` `String` 类
> 
> 这些类不能被继承，自然不能被重写

### 多态

利用多态可以增加程序的灵活性，减少代码量，让逻辑更符合直觉

比如想实现一个输出职业的效果，当然可以这么写

```java
public static void job(Student student) {
    System.out.println("这是个学生");
}
public static void job(Teacher teacher) {
    System.out.println("这是个老师")
}
public static void job(Worker worker) {
    System.out.println("这是个工人")
} //上面利用了方法的重载，没看懂的回去看
```

其实可以利用向上转型来写，更加符合直觉

```java
public static class Jobs {}
public static class Student extends Jobs {}
public static class Teacher extends Jobs {}
public static class Worker extends Jobs {}

public static void job(Jobs aJob) {
    if (aJob instanceof Student)
        System.out.println("这是个学生");
    else if (aJob instanceof Teacher)
        System.out.println("这是个老师");
    else if (aJob instanceof Worker)
        System.out.println("这是个工人");
}

public static void main(String[] args) {
    job(new Student());
    job(new Teacher());
    job(new Worker());
}
```

> 这里把不同的类向上转型为父类，再通过 `instanceof` 判断对象的类型分辨子类
> 
> 这样就可以直接传入同一父类下不同子类的对象，更加符合直觉

### abstract 关键字

使用 `abstract` 关键字修饰的类被称为抽象类

使用 `abstract` 关键字修饰的方法被称为抽象方法

抽象方法没有方法体

抽象类没有意义

使用 `abstract` 关键字修饰的类和方法要求必须被继承并在子类中被重写 

由于这种特性，一般把父类写作抽象类，再让子类实现

```java
public static abstract class Human {
    public abstract void printJob();
} //看得出来这玩意确实一点意义都没有

public static class Student extends Human {
    @Override
    public void printJob() {
        System.out.println("这是个学生");
    }
}

public static void main(String[] args) {
    Student me = new Student();
    //Human a = new Human();
    //这样写会报错，因为 Human类 是抽象的，无法实例化
    me.printJob();
}
```

> 这会要求一些不需要 `printJob` 方法的子类也要重写这个方法，造成代码冗余
> 
> 如果把父类分为几个类，一部分有 `printJob` 方法，一部分有其他需要的方法
> 
> 让子类按照需要继承父类就行，这种方法看似解决了问题
> 
> 但是这样会引发另一个问题：一个类不能继承多个父类
> 
> 所以人们为了应对这种情况，引入了接口的概念

### 接口

#### 声明一个接口

接口是抽象类的延伸，可以把它看作纯粹的抽象类

接口中的所有方法都没有方法体

使用 `interface` 关键字定义一个接口

```java
public interface <接口名> {
    void <方法名>();
}
```

> 接口里面的方法必须是 `public` 或 `abstract` 类型的，默认是 `public`

#### 实现一个接口

接口的优点在于一个类在继承一个父类的同时可以实现一个接口

```java
//公开的 静态的 类   学生类   继承自  人类   实现      行为接口
public static class Student extends Human implements Run {
    @Override
    public void run() {
        System.out.println("###有个学生在跑");
    }
}

public static class Teacher extends Human implements Speak {
    @Override
    public void speak() {
        System.out.println("有个老师在讲话");
    }
}

//这里实现了两个方法，中间使用逗号隔开
public static class Me extends Student implements Speak, Run {
    @Override
    public void speak() {
        System.out.println("我能讲话");
    }
    @Override
    public void run() {
        System.out.println("我能跑");
    }
}

public static class Human {}

//两个接口
public interface Speak {
    public void speak();
}
public interface Run {
    public void run();
}

public static void main(String[] args) {
    Student stu1 = new Student();
    Teacher teach1 = new Teacher();
    Me me = new Me();
    stu1.run();
    teach1.speak();
    me.speak();
    me.run();
}
```

> 可以看到，上面的例子体现了接口的几个特性
> 
> 例子中定义了两个接口，分别包含了两个方法
> 
> `Teacher` 类实现了 `Speak` 接口里面的方法
> 
> `Student` 类实现了 `Run` 接口的方法
> 
> `Me` 类实现了两个接口的方法
> 
> 每个类可以根据自己的需求，实现不同的接口，让程序更灵活
> 
> 同时它们都继承自 `Human` 类，保证了程序结构关系

#### 接口继承接口

接口继承接口时不使用 `implements` ，而是使用 `extends`

```java
public interface Action {}
public interface Speak extends Action {
    public void speak();
}
```

> 注意在实现子接口时，必须重写所有父接口的方法
> 
> ~~感觉这玩意不是很实用~~

#### 抽象类和接口的区别

二者在许多方面相似，但也有明显的不同

* 抽象类和接口都可以有子类

* 抽象类通常是子类的 “模板”，接口通常是描述子类的 “行为”

* 子类虽然只能继承一个抽象类，但是能实现多个接口

* 创建抽象类使用 `abstract` 关键字

* 创建接口使用 `interface` 关键字

* 抽象类的方法必须使用 `abstract` 修饰，接口的方法可以省略

* 接口没有构造方法，抽象类可以有

* 子接口可以继承多个父接口，但是子抽象类只能继承一个父抽象类

---

## 包和内部类

#### 类名冲突

如果一个程序只由一个类组成，通常不会出现类名冲突的问题，毕竟都是自己写的

但是在大型项目或者联合项目时，经常会出现类名冲突问题

例如：一个项目里面有两个部分，都有 `Login` 类，分别给两个人写，这两个人都给类起了同一个名字，在合并项目的时候，就会出现类名冲突的问题

为了应对这个问题，人们提出了 类包 的概念

### 完整的类路径

在我们写程序的时候，经常会使用 `String` 类

实际上 `String` 类并不是它的完整名字，完整的应该是 `java.lang.String`

再比如说在一个程序中同时使用

```java
java.ulti.Date
java.sql.Date
```

这两个 `Date` 类，可以通过指定完整的类路径来使用

```java
java.ulti.Date date1 = new java.ulti.Date();
java.sql.Date date2 = new java.sql.Date(1000);
```

### 创建包

每个编译器里面创建包的方式不同，自己去查

`Intellij IDEA` 是在 `src` 目录下新建 `软件包` ，这个所谓的软件包就是类包，软件包的名字就是包名

当你在软件包里面新建类的时候，IDEA 会帮你加上包声明，例如

```java
package <刚刚的包名>;

public class <类名> {
    //代码块
}
```

如果编译器没有帮你加上报名，你也应该在这个类的前面声明包名

`package <包名>;`

> 它一定是在一个类的最前面

### 导入包

如果你使用的是 `Intellij IDEA` ，应该已经注意到了，当你使用某些类时，编译器会帮你导入你调用的这个类的包，比如说当你使用了 `Scanner` 类的时候，会加上：

```java
import java.util.Scanner;
```

这就是导入包的标准方式

```java
//如果你想使用这个包里面的所有类
import <完整的包路径>.*;
//如果你只想使用这个包里面的某个类
import <完整的包路径>.<类名>;
```

### 导入静态成员

既然可以导入包里面的某个类，同样也可以导入包里的某个静态成员（静态成员和类同级）

这里有一种常见的偷懒方法

```java
import static java.lang.System.out;

public class Example {
    public static void main(String[] args) {
        //因为已经指定了是 System类 里面的 out 方法，所以可以省去 System.
        out.println("这是一个例子");
    }
}
```

### 内部类

当一个类定义在另一个一个类里面的时候

外面的类叫做外部类，里面的类叫做内部类

#### 成员内部类

这个不用多讲，你平时在主类里面写的类都是成员内部类，你只需要记住几个特点

* 成员内部类可以直接调用外部类的 `private` 类型的成员

* 内部类的实例一定是绑定在外部类的实例上的
  
  * 你平时写的类都是绑定在主类的实例上的

* 如果外部类和内部类有重名的变量，使用 `this.` 可以调用内部类的变量
  
  * 使用 `<外部类名>.` 可以调用外部类的变量

#### 匿名内部类

这是一种在创建类的时候使用的一种写法，特点是现用现写

```java
//声明一个类
public static abstract class Human {
    abstract void show();
}

public static void main(String[] args) {
    Human me = new Human() {
        //在创建对象的时候当场实现方法
        public void show() {
            System.out.println("这是一个例子");
        }
    };
    me.show();
}
```

这里可以发现，一个抽象类不仅能实例化，而且可以调用抽象方法

实际上，`me` 并不是 `Human` 类的对象，而是一个继承自 `Human` 类，实现了 `Human` 类的抽象方法的匿名类

这种方法可以让程序更加灵活

需要注意的：

* 匿名类不能有构造方法

* 匿名类不能定义静态成员

* 如果匿名类创建的对象没有赋值给任何引用变量，会导致 `JVM` 在使用一次以后就销毁这个对象

## 结语

Java 的基础部分到这里就结束了，后续应该会写另外写 `Java核心技术.md`

HaiMFeng

2024.11.6

[GitHub @Hai-M-Feng](https://github.com/Hai-M-Feng)
