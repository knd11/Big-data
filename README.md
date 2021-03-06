# VS Code + Java

## VS Code快捷键

```shell
Alt + Up : 上移选中代码
Fn + home/end ：快速到达行首或行尾

Ctrl + +/-:放大或缩小当前 光标选择的位置
Ctrl + B : 隐藏/展开左侧菜单
Ctrl + G : 挑到指定行号
Ctrl + T : 查看选中类或方法的源码

Ctrl + w : 关闭当前窗口
Ctrl + Shift+ w : 关闭当前窗口
Ctrl + D : 复制当前行代码

Ctrl + Home/End : 光标在单词间移动
Ctrl + Shift + Home/End : 选中光标👈或👉边的单词

Ctrl + Shift + k : 删除当前行
Ctrl + Shift + X : 将小写变为大写
Ctrl + Shift + P  + "New Java Project" ： 新建Java项目 
Ctrl + Shift + O 自动导包/在源码中查找类
```

在vscode中导入IDEA的快捷键包，可用下列快捷键

```shell
fori  : 生成变量为i的for循环
Alt + enter : 创建对象
```

IDEA快捷键：

```shell
想要输出内容.sout ： 打印输出内容
Alt + Shift + Up/Down : 将选中代码上/下移

Ctrl + Shift + - ： 折叠所有代码
Ctrl + Shift + + ： 展开所有代码
Ctrl + Shift + A :  搜索全局，比如搜索toolbar可快捷打开toolbar

Ctrl + Alt + B：查看源码
Ctrl + Alt + T: surround with，比如 try-catch,if-else等
Ctrl + Shift + S： Linux 下Ctrl + Alt + T与打开终端的 快捷键冲突。

Shift + Esc ：折叠左侧Project文件浏览窗口

F4：查看源代码
Ctrl + H: 查看当前类的继承关系
Ctrl + N：全局搜索
Ctrl + F12：查看当前方法目录
Ctrl + Alt  + U : Show Diagram popu
Ctrl + Shift + E：访问最近写代码的位置
```



## VS Code使用JUnit

The `Test` annotation tells JUnit that the `public void` method to which it is attached can be run as a test case. To run the method, JUnit first constructs a fresh instance of the class then invokes the annotated method. Any exceptions thrown by the test will be reported by JUnit as a failure. If no exceptions are thrown, the test is assumed to have succeeded.

A simple test looks like this:

```java
import org.junit.Test;
public class Example {
    @Test
    public void method() {
       org.junit.Assert.assertTrue( new ArrayList().isEmpty() );
    }
}
```

```java
//若JUnit找不到包，界面不能运行，提示缺少main方法，在.project中nature标签处 加上下面语句：
	<natures>
		<nature>org.eclipse.jdt.core.javanature</nature>
	</natures>
//并在.classpath中 src和bin设置的中间 加上下面语句
<classpathentry kind="con" path="org.eclipse.jdt.junit.JUNIT_CONTAINER/4"/>

//更简单的方式是直接复制别的项目的.classpath 和.project文件
```



##创建包

报错：[The declared package does not match the expected package Java](https://www.cnblogs.com/linux-centos/p/10784037.html)

用创建文件夹的形式创建包 如com/atguigu/java后，要先将当前文件添加到路径后才能正确导包。选中Java文件，Add foder to Java source path.

##vscode 目录树的缩进设置

[![img](pic/c2fdfc039245d6880c54608eabc27d1ed21b2442.png)](https://iknow-pic.cdn.bcebos.com/c2fdfc039245d6880c54608eabc27d1ed21b2442)

文件-设置-首选项-搜索 treein ，改一下控制树缩进就好

##html

插件：

```
HTML CSS Support
HTML Snippets
HTML Preview
open in browser
```

# Java basic

## Java学习的三条主线

```mermaid
graph LR
    Java --> 类和类的成员;
    Java --> 面向对象的三大特征;
    Java --> 关键字;
    
    类和类的成员 --> 属性;
    类和类的成员 --> 方法;
    类和类的成员 --> 构造器;
    
    面向对象的三大特征 --> 封装
    面向对象的三大特征 --> 继承
    面向对象的三大特征 --> 多态
```



​	

#### 数组

基本数据类型的值传递 ：值传递

引用数据类型（字符串、数组）的的传递：地址传递

#### Object 类

##### == 和 equals() 的区别

<u>基本数据类型用==，引用数据类型用equals()</u>。

 \* ====== 运算符 :

- 1. 以使用在基本数据类型变量和引用数据类型变量中

  2. 如果比较的是基本数据类型变量：比较两个变量保存的数据是否相等。（不一定类型要相同）

  3. 如果比较的是引用数据类型变量：比较两个对象的地址值是否相同.即两个引用是否指向同一个对象实体

     \* 补充： == 符号使用时，必须保证符号左右两边的变量类型一致。

==equals()方法==

- 1. 是一个方法，而非运算符

  2. 只能适用于引用数据类型

  3. Object类中equals()的定义：

     ```java
     public boolean equals(Object obj) {
           return (this == obj);
     }
     ```

     说明：Object类中定义的equals()和==的作用是相同的：比较两个对象的地址值是否相同.即两个引用是否指向同一个对象实体

  4. 像==String、Date、File、包装类等==都重写了Object类中的equals()方法。重写以后，比较的不是两个引用的地址是否相同，而是比较两个对象的"实体内容"是否相同。

  5. 通常情况下，我们自定义的类如果使用equals()的话，也通常是比较两个对象的"实体内容"是否相同。那么，我们就需要对Object类中的equals()进行重写

  6. ==重写==的原则：比较两个对象的"实体内容"（属性）是否相同.==注意是重写==

### 1. 类



类的成分：属性、方法、构造器

| 权限修饰符 | 类内部 | 同一个包 | 不同包的==子类== | 同一个工程 |
| ---------- | ------ | -------- | ---------------- | ---------- |
| private    | √      |          |                  |            |
| 缺省       | √      | √        |                  |            |
| protected  | √      | √        | √                |            |
| public     | √      | √        | √                | √          |
|            |        |          |                  |            |

重载（overload）和重写（override/overwrite）的区别:

1. 概念
2. 具体规则
3. 重写表现为多态性（晚绑定），重载（早绑定）不表现

#### 包装类

为了让基本数据类型更强大，引入了包装类。变成类以后就具有了类的特征

| **基本数据类型** |      | byte | short | int     | long | float | double | boolean | char |
| ---------------- | ---- | ---- | ----- | ------- | ---- | ----- | ------ | ------- | ---- |
| **包装类**       |      | Byte | Short | Integer | Long | Float | Double | Boolean | Char |

包装类的父类是Number

##### 包装类的转换

```mermaid
graph LR
    基本数据类型 --自动装箱-->包装类
    包装类--自动拆箱-->基本数据类型
    
    基本数据类型/包装类 --String.valueOf--> String类型
    String类型--包装类的parseXxx--> 基本数据类型/包装类
    
    String类型--String的toCharArray-->char数组
    char数组 --String的构造器--> String类型
    
    String类型--String的getBytes-->Bytes数组
    Bytes数组 --String的构造器--> String类型
```

- String类型 --->基本数据类型、包装类：调用包装类的parseXxx(String s)

  JDK 5.0 新特性：==自动装箱== 与==自动拆箱==

```java
//自动装箱：基本数据类型 --->包装类
int num2 = 10;
Integer in1 = num2;//自动装箱
		
boolean b1 = true;
Boolean b2 = b1;//自动装箱
		
//自动拆箱：包装类--->基本数据类型
System.out.println(in1.toString());
int num3 = in1;//自动拆箱
```

- 基本数据类型、包装类--->String类型：调用String重载的valueOf(Xxx xxx)

  ```java
  int num1 = 10;
  //方式1：连接运算
  String str1 = num1 + "";
  //方式2：调用String的valueOf(Xxx xxx)
  float f1 = 12.3f;
  String str2 = String.valueOf(f1);//"12.3"
  Double d1 = new Double(12.4);
  String str3 = String.valueOf(d1);
  ```

  - String类型 --->基本数据类型、包装类：调用包装类的parseXxx(String s)

    ```java
    String str1 = "123";
    //错误的情况：
    //int num1 = (int)str1;
    //Integer in1 = (Integer)str1;
    //可能会报NumberFormatException
    int num2 = Integer.parseInt(str1);
    System.out.println(num2 + 1);
    
    String str2 = "true1";
    boolean b1 = Boolean.parseBoolean(str2);
    ```

    [面试题](#1.包装类)

#### 代码块

- 代码块的作用：用来初始化类、对象
- 代码块如果有修饰的话，只能使用static.
- 分类：静态代码块  vs 非静态代码块
- - ==静态代码块==
  - - 内部可以有输出语句
    - 随着类的加载而执行,而且只执行一次
    - 作用：初始化类的信息
    - 如果一个类中定义了多个静态代码块，则按照声明的先后顺序执行
    - 静态代码块的执行要优先于非静态代码块的执行
    - 静态代码块内只能调用静态的属性、静态的方法，不能调用非静态的结构
- - ==非静态代码块==
    - 内部可以有输出语句
    - 随着对象的创建而执行
    - 每创建一个对象，就执行一次非静态代码块
    - 作用：可以在创建对象时，对对象的属性等进行初始化
    - 如果一个类中定义了多个非静态代码块，则按照声明的先后顺序执行
    - 非静态代码块内可以调用静态的属性、静态的方法，或非静态的属性、非静态的方法

==对属性可以赋值的位置==（执行顺序：1 - 2/5 - 3 - 4 ，2和5的顺序看它们排放的顺序）

- 1. 默认初始化（静态）
- 1. 显式初始化（类内开始的地方初始化，且赋值。eg. int a = 5;）
- 1. 构造器中初始化
- 1. 有了对象以后，对象.属性 或对象.方法
- 1. 在<u>代码块</u>中赋值

静态代码块的应用情景：属性中不能对数值进行操作，如：`int a; a=1;`是错的。有些赋值想要是一次性的，不能写在方法中，也不能写在属性中，于是就有了静态代码块。既能只给对象赋值一次，又能调静态方法。

#### 内部类

- Java中允许将一个类A声明在另一个类B中，则类A就是内部类，类B称为外部类

- 内部类的分类：成员内部类（静态、非静态）  vs 局部内部类(方法内、代码块内、构造器内)

- ==成员内部类==： 

- - - 一方面，作为外部类的成员：
    - - - 调用外部类的结构
        - 可以被static修饰
        - 可以被4种不同的权限修饰
    - 另一方面，作为一个类：
    - - - 类内可以定义属性、方法、构造器等
        - 可以被final修饰，表示此类不能被继承。言外之意，不使用final，就可以被继承
        - 可以被abstract修饰

- 关注如下的3个问题：

  - 如何实例化成员内部类的对象

    //静态成员内部类

    Person.Dog dog = new Person.Dog();

    //非静态成员内部类

    Person p = new Person();

    Person.Bird bird = new p.Bird bird ();

  - 如何在成员内部类中区分调用外部类的结构

  - 开发中局部内部类的使用  见《InnerClassTest1.java》

在局部内部类的方法中（比如：show）如果调用局部内部类所声明的方法(比如：method)中的局部变量(比如：num)的话, 要求此局部变量声明为final的。

​     \* jdk 7及之前版本：要求此局部变量显式的声明为final的

​     \* jdk 8及之后的版本：可以省略final的声明

### 2. 面向对象的三大特征

#### 2.1 封装性

#### 2.2 继承性

继承格式：权限修饰符 + class + 子类名 + extends 父类名

==super== : 在子类中，当子类和父类的属性或方法出现重叠时，既想显示父类又想要子类就用super代表父类，this代表子类（默认是子类）。如：

```java
//假设子类(id=1002)和父类(id=1001)中都有id
System.out.println(id);//1002
System.out.println(this.id);//1002
System.out.println(super.id);//1001
```

super还可以调用父类中的构造器：

```java
super(name,age);
```

类的构造器中 this(形参列表) 和 super(形参列表) 只能二选一。

super可以继承父类的属性、方法、构造器

继承的时候，父类的形参列表是(int a , int... arr),子类的形参列表是(int a ,int[] arr)，也是可以用重写的

#### 2.3 多态性

对象的多态性，父类的引用指向子类的对象

```java
Person p = new Man();
```

多态的使用：当调用子父类同名同参数的方法时，编译是认为是父类的方法，执行时执行子类方法（实际执行的是子类重写父类的方法） ---==虚拟方法调用==



对象的多态性，只适用于方法，不适用于属性：

==方法== ： 编译看左边，运行看右边

==属性== ：编译和运行都看左边



多态是运行时行为(真正运行时才知道真正new的是谁)，详见InterViewTest.java



==早绑定/静态绑定==： 对于重载来说，在方法调用之前，编译器就已经确定了要调用的方法。

==晚绑定/静态绑定==： 对于多态，只有到方法调用的那一刻，解释运行器才知道索要调用的具体方法。



```mermaid
graph LR
    父类--向下转型:instance of-->子类;
    子类--向上转型:多态-->父类;
```

- **向上转型** : 通过子类对象(小范围)实例化父类对象(大范围),这种属于自动转换

  当我们需要多个同父的对象调用某个方法时,通过向上转换后,则可以确定参数的统一.方便程序设计

  ==向上转型时==(注意条件),父类只能调用父类方法或者子类覆写后的方法,而子类中的单独方法则是无法调用的。

- **向下转型** : 通过父类对象(大范围)实例化子类对象(小范围),这种属于强制转换

  向下转型则是为了,通过父类强制转换为子类,从而来调用子类<u>独有的方法</u>



为了避免在向下转型时出现异常，在向下转型前先用instanceof 判断

==A instanceof B== : 判断A是否是B 或者B的实例



### 3. 关键字

#### static:静态的

- static可以用来修饰：==属性、方法、代码块、内部类==

- 使用static修饰属性：静态变量（或类变量）

- - - 属性，按是否使用static修饰，又分为：静态属性  vs 非静态属性(实例变量)
    - - ==实例变量==：我们创建了类的多个对象，每个对象都独立的拥有一套类中的非静态属性。当修改其中一个对象中的非静态属性时，不会导致其他对象中同样的属性值的修改。
      - 静态变量：我们创建了类的多个对象，多个对象共享同一个静态变量。当通过某一个对象修改静态变量时，会导致其他对象调用此静态变量时，是修改过了的。

- static修饰属性的其他说明：

  ① 静态变量随着类的加载而加载。可以通过"类.静态变量"的方式进行调用

  ② 静态变量的加载要早于对象的创建。

  ③ 由于类只会加载一次，则静态变量在内存中也只会存在一份：存在方法区的静态域中。

  ④

  |      | 类变量 | 实例变量 |
  | ---- | ------ | -------- |
  | 类   | yes    | no       |
  | 对象 | yes    | yes      |

- - - 静态方法中，只能调用静态的方法或属性  (==静态属性==举例：System.out;  Math.PI;)
  - - 非静态方法中，既可以调用非静态的方法或属性，也可以调用静态的方法或属性

- static注意点：

- - - 在静态的方法内，不能使用this关键字、super关键字。==this();super();可分别调用当前;父类的的构造器==
  - - 关于静态属性和静态方法的使用，大家都从生命周期的角度去理解。

- 开发中，如何确定一个==属性==是否要声明为static的？
- - - 属性是可以被多个对象所共享的，不会随着对象的不同而不同的。
- - - 类中的常量也常常声明为static
- 开发中，如何确定一个==方法==是否要声明为static的？
- - - 操作静态属性的方法，通常设置为static的
    - 工具类中的方法，习惯上声明为static的。 比如：Math、Arrays、Collections



#### main

 \* 1. main()方法作为程序的入口

 \* 2. main()方法也是一个普通的静态方法

 \* 3. main()方法可以作为我们与控制台交互的方式。（之前：使用Scanner）

```shell
//去掉包名，在命令行中执行下面语句也是可以的
javac MainDemo.java
java MainDemo  22 33 44
```

#### final

- final可以用来修饰的结构：==类、方法、变量==
- final 用来修饰一个==类==:此类不能被其他类所继承。比如：==String类、System类、StringBuffer类==
- final 用来修饰==方法==：表明此方法不可以被重写，比如：==Object类中getClass()==
- final 用来修饰==变量==：此时的"变量"就称为是一个常量
- - - final修饰<u>属性</u>：可以考虑赋值的位置有：==显式初始化、代码块中初始化、构造器中初始化==
    - final修饰<u>局部变量</u>：
    - - - 尤其是使用final修饰<u>形参</u>时，表明此形参是一个常量。当我们调用此方法时，给常量形参赋一个实参。一旦赋值以后，就只能在方法体内使用此形参，但不能进行重新赋值。
- static final 用来修饰属性：全局常量

#### abstract -- 抽象类与抽象方法

- abstract可以用来修饰的结构：==类、方法==

- abstract修饰类：抽象类

- - - 此类不能实例化（不能建对象）
    - 抽象类中一定有构造器，便于子类实例化时调用（涉及：子类对象实例化的全过程）
    - 开发中，都会提供抽象类的子类，让子类对象实例化，完成相关的操作

- abstract修饰方法：抽象方法

- - - 抽象方法只有方法的声明，没有方法体

    - 包含抽象方法的类，一定是一个抽象类。反之，抽象类中可以没有抽象方法的

    - 若子类重写了父类中的所有的抽象方法后，此子类方可实例化

      若子类没有重写父类中的所有的抽象方法，则此子类也是一个抽象类，需要使用abstract修饰

- abstract不能用来修饰私有方法、静态方法、final的方法、final的类



#### Interface -- 接口

- 接口使用interface来定义
- Java中，接口和类是并列的两个结构
- 如何定义接口：定义接口中的成员
- - JDK7及以前：只能定义全局常量和抽象方法
- - - - 全局常量：==public static final==的.但是书写时，可以省略不写
    - - 抽象方法：==public abstract== 的
- - JDK8：除了定义全局常量和抽象方法之外，还可以定义==静态方法、默认方法==（略）
  - - - 接口中定义的全局常量只能接口用，不能通过实现该接口的类的对象用
      - 通过实现类的对象，可以调用接口中的默认方法。若对象重写了默认方法，则执行的是重写的方法
      - 如果子类(或实现类)继承的  父类 和 实现的接口 中声明了同名同参数的<u>默认方法</u>(不是属性)，那么子类在<u>没有重写</u>此方法的情况下，默认调用的是父类中的同名同参数的方法。-->类优先原则
      - 如果实现类实现了多个接口，而这多个接口中定义了同名同参数的默认方法，那么在实现类没有重写此方法的情况下，报错。-->接口冲突。这就需要我们必须在实现类中重写此方法
- 接口中不能定义构造器的！意味着接口不可以实例化
- Java开发中，接口通过让类去实现(==implements==)的方式来使用
- - - 如果实现类覆盖了接口中的所有抽象方法，则此实现类就可以实例化
    - 如果实现类没有覆盖接口中所有的抽象方法，则此实现类仍为一个抽象类
- Java类可以实现多个接口   --->弥补了Java单继承性的局限性
- - - class AA extends BB implements CC,DD,EE
- 接口与接口之间可以继承，而且可以多继承

```mermaid
graph LR
	类 -- 继承 --> 类
	类 -- 实现 --> 接口
	接口 -- 继承 --- 继承
```

- 接口的具体使用，体现多态性
- 接口，实际上可以看做是一种规范

# Java Senior

## 异常处理

```mermaid
graph LR
	Java源程序--javac.exe-->字节码文件
	Java源程序-.编译时错误.-字节码文件

	字节码文件--java.exe-->在内存中加载/运行类
	字节码文件-.运行时错误.-在内存中加载/运行类
	
```

### 异常体系结构

 \* 

 \* java.lang.Throwable

 \*      |-----java.lang.Error:一般不编写针对性的代码进行处理。

 \*      |-----java.lang.Exception:可以进行异常的处理

 \*          |------编译时异常(checked)

 \*                  |-----IOException

 \*                      |-----FileNotFoundException

 \*                  |-----ClassNotFoundException

 \*          |------运行时异常(unchecked,RuntimeException)

 \*                  |-----NullPointerException

 \*                  |-----ArrayIndexOutOfBoundsException

 \*                  |-----ClassCastException

 \*                  |-----NumberFormatException

 \*                  |-----InputMismatchException

 \*                  |-----ArithmeticException

### 异常处理机制

##### 1. try-catch-finally

- 过程一：=="抛"==：

  程序在正常执行的过程中，一旦出现异常，就会在异常代码处生成一个对应异常类的对象。并将此对象抛出。 一旦抛出对象以后，其后的代码就不再执行。

- - - - 关于异常对象的产生：

        ① 系统自动生成的异常对象

        ② ==手动==的生成一个异常对象，并抛出（==throw==）​         

- 过程二：=="抓"==：可以理解为异常的处理方式：① try-catch-finally  ② ==throws==

- try-catch-finally的使用

  ```java
   * try{
   * 		//可能出现异常的代码
   * 
   * }catch(异常类型1 变量名1){
   * 		//处理异常的方式1
   * }catch(异常类型2 变量名2){
   * 		//处理异常的方式2
   * }catch(异常类型3 变量名3){
   * 		//处理异常的方式3
   * }
   * ....
   * finally{
   * 		//一定会执行的代码
   * }
  ```

  - 1. finally是可选的。
  - 1. 使用try将可能出现异常代码包装起来，在执行过程中，一旦出现异常，就会生成一个对应异常类的对象，根据此对象的类型，去catch中进行匹配
  - 1. 一旦try中的异常对象匹配到某一个catch时，就进入catch中进行异常的处理。一旦处理完成，就跳出当前的 try-catch结构（在没有写finally的情况）。继续执行其后的代码
  - 1. catch中的异常类型如果没有子父类关系，则谁声明在上，谁声明在下无所谓。如果满足子父类关系，则要求子类一定声明在父类的上面。否则，报错
  - 1. 常用的异常对象处理的方式： ① String  getMessage()    ② printStackTrace()
  - 1. 在try结构中声明的变量，再出了try结构以后，就不能再被调用
  - 1. try-catch-finally结构可以嵌套
    2. finally中声明的是一定会被执行的代码。即使catch中又出现异常了，try中有return语句，catch中有return语句等情况。
    3. 像<u>数据库连接、输入输出流、网络编程Socket等资源</u>，JVM是不能自动的回收的，我们需要自己手动的进行资源的释放。此时的资源释放，就需要声明在finally中。



- 体会1：使用try-catch-finally处理编译时异常，是得程序在编译时就不再报错，但是运行时仍可能报错。相当于我们使用try-catch-finally将一个编译时可能出现的异常，延迟到运行时出现。
- 体会2：开发中，由于运行时异常比较常见，所以我们通常就不针对运行时异常编写try-catch-finally了。针对于编译时异常，我们说一定要考虑异常的处理。

##### 2.throws+异常类型

1. "throws + 异常类型"写在方法的声明处。指明此方法执行时，可能会抛出的异常类型。一旦当方法体执行时，出现异常，仍会在异常代码处生成一个异常类的对象，此对象满足throws后异常类型时，就会被抛出。异常代码后续的代码，就不再执行！

2. 体会：try-catch-finally:真正的将异常给处理掉了。throws的方式只是将异常抛给了方法的调用者。  并没有真正将异常处理掉。 

3. 子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常类型

4. 开发中如何选择使用try-catch-finally 还是使用throws？

   4.1 如果父类中被重写的方法没有throws方式处理异常，则子类重写的方法也不能使用throws，意味着如果子类重写的方法中有异常，必须使用try-catch-finally方式处理。

   4.2 执行的方法a中，先后又调用了另外的几个方法，这几个方法是递进关系执行的。我们建议这几个方法使用throws的方式进行处理。而执行的方法a可以考虑使用try-catch-finally方式进行处理。

5. 

##### 3.如何自定义异常类

- 继承于现有的异常结构：RuntimeException 、Exception
- 提供全局常量：serialVersionUID
- 提供重载的构造器

## IntelliJ与多线程

**IntelliJ 配置**

- 鼠标滚轮放大字体

  Editor --> Genneral --> Mouse -->change fontsize(Zoom)....

- 鼠标悬浮提示

  Editor --> Genneral -->Show quick documentation on mouse move

- 自动导包

  Insert imports on paste:All

  Editor --> Genneral -->auto Import -->选择：

  Add unambiguous imports on the fly
  Optimize imports on the fly(for current project)

- 显示分隔符

  Editor --> Genneral -->Apperence-->Show method separators

- 设置取消单行显示tabs的操作

  Editor --> Genneral -->Editor Tabs -->Show tabs in one row

- 注解

  Editor  -->File and Code Templates --> Include -->File Header -->输入：

  ```java
  /**
      @author cxy
      @create ${YEAR}-${MONTH}-${DAY}-${TIME}
  */
  ```

- 更改编码方式

  Editor --> Genneral -->Code Style -->File Encoding-->全部改为UTF-8

  勾选Transparent native-to-ascii conversion

- 自动编译

  Build,Execution,Deployment --> Compiler -->勾选

  Compile independent modules in parallel 
  Rebuild module on dependency change





| software | Eclipse   | IntelliJ idea |
| -------- | --------- | ------------- |
| 等价     | workspace | project       |
| 等价     | project   | module        |

==线程==： 一条*线程* 指的是进程中一个单一顺序的控制流，是操作系统能够进行运算调度的最小单位。

==进程==：是计算机中的程序关于某数据集合上的一次运行活动，是系统进行资源分配和调度的基本单位。一个进程包含多个线程。

==CPU==：

- 单核CPU：假的多线程，一个时间单元内只能执行一个线程的任务，其它任务虽打开，但被挂起。
- 多核CPU：一个时间单元内能执行多个线程的任务

==并行==: 多个CPU同时执行多个任务

==并发==: 一个CPU（采用时间片）同时执行多个任务，如秒杀

**多线程的优点**

1. 提高应用程序的响应
2. 提高CPU的利用率
3. 改善程序结构

### 1. 多线程的创建方式

#### 1.1 继承于Thread类

```
 * 1. 创建一个继承于java.lang.Thread类的子类
 * 2. 重写Thread类的run() --> 将此线程执行的操作声明在run()中
 * 3. 创建Thread类的子类的对象
 * 4. 通过此对象调用start()  
```

- start 方法的作用：①启动当前线程 ② 调用当前线程的run()
- 我们不能通过直接调用 run() 的方式启动线程
- 不可以让已经start()的线程去执行，会报IllegalThreadStateException。需要重新创建一个线程的对象

**Thread类中常用方法** 

1. start():启动当前线程；调用当前线程的run()
2. run(): 通常需要重写Thread类中的此方法，将创建的线程要执行的操作声明在此方法中
3. currentThread():静态方法，返回执行当前代码的 *线程* 
4. getName():获取当前线程的名字
5. setName():设置当前线程的名字
6. yield():释放当前CPU的执行权
7. join():在线程a中调用线程b的join(),此时线程a就进入阻塞状态，直到线程b完全执行完以后，线程a才结束阻塞状态。
8. stop():已不用了。当执行此方法时，强制结束当前线程
9. sleep(long millitime):让当前线程“睡眠”指定的millitime毫秒。在指定的millitime毫秒时间内，当前线程是阻塞状态。
10. isAlive():判断当前线程是否存活

**线程的优先级**

- 1.1 

- - - MAX_PRIORITY：10
  - - MIN _PRIORITY：1
  - - NORM_PRIORITY：5  -->默认优先级

  1.2 如何获取和设置当前线程的优先级

- - - getPriority():获取线程的优先级
  - - setPriority(int p):设置线程的优先级

- 说明：高优先级的线程要抢占低优先级线程cpu的执行权。但是只是从概率上讲，高优先级的线程高概率的情况下被执行。并不意味着只有当高优先级的线程执行完以后，低优先级的线程才执行

#### 1.2. 实现Runnable接口

- 创建一个实现了Runnable接口的类

- 实现类去实现Runnable中的抽象方法：run()

- 创建实现类的对象

- 将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象

- 通过Thread类的对象调用start() 。==谁start了 线程就是谁的==


**方式比较:  继承于Thread类 vs. 实现Runnable接**口

- 开发中：优先选择：实现Runnable接口的方式

  ​	原因：1.  实现的方式没有类的单继承性的局限性

  ​		    2. 实现的方式更适合来处理多个线程有==共享数据==的情况。

- 联系：public class Thread implements Runnable，==Thread本身也实现了Runnable接口==（因为Thread的子类可以实现Runnable接口）

- 相同点：两种方式都需要重写run(),将线程要执行的逻辑声明在run()中。


#### 1.3 实现Callable接口。 

--- JDK 5.0新增

- call()可以有返回值
- call()可以抛出异常，被外面的操作捕获，获取异常的信息
-  Callable支持泛型

- 步骤

- 1. 创建一个实现Callable的实现类
  2. 实现 call 方法，将此线程需要执行的操作声明在call()中
  3. 创建Callable接口实现类的对象
  4. 将此Callable接口实现类的对象作为传递到FutureTask构造器中，创建FutureTask的对象
  5. 将FutureTask的对象作为参数传递到Thread类的构造器中，创建Thread对象，并调用start()
  6. 获取Callable中call方法的返回值（可省，看具体情况）

#### 1.4 线程池

- 创建步骤

- 1. 提供指定线程数量的线程池
  2. 设置线程池的属性
  3. 执行指定的线程的操作。需要提供实现Runnable接口或Callable接口实现类的对象execute
  4. 关闭连接池 shutdown()

[面试题3](#3 创建多线程有几种方式？)





### 2. 线程的生命周期

生命周期：某个线程从出生到消亡这段时间

关注 ：状态 a --> 状态 b ：哪些方法执行了（去重写回调方法）

​		 某个方法主动调用导致  状态 a --> 状态 b 

阻塞：临时状态，不可以作为最终状态（死亡）

### 3. 线程的同步

- 线程安全问题之所以会出现，是因为有数据共享，比如账户。

- 在Java中，我们通过同步机制，来解决线程的安全问题。

- - 1. ==方式一：同步代码块==

       ```java
       synchronized(同步监视器){
           //需要被同步的代码
       }
       ```

       - 说明：

       - - 1. 操作共享数据的代码，即为需要被同步的代码。  -->包含代码不能多了，也不能少了。

         - 2. ==共享数据==：多个线程共同操作的变量。比如：ticket就是共享数据

           3. ==同步监视器==，俗称：==锁==。任何一个类的对象，都可以充当锁。

              要求：==<u>多个线程必须要共用同一把锁</u>==，即同一个对象。

       - 补充：在实现Runnable接口创建多线程的方式中，我们可以考虑使用this充当同步监视器。

       - 好处:  同步的方式，解决了线程的安全问题。

       - 局限性:  操作同步代码时，只能有一个线程参与，其他线程等待。相当于是一个单线程的过程，效率低。

    2. ==方式二：同步方法==

       如果操作共享数据的代码完整的声明在一个方法中，我们不妨将此方法声明同步的。

       -  \*  1. 同步方法仍然涉及到同步监视器，只是不需要我们显式的声明。

       - \*  2. 非静态的同步方法，同步监视器是：this

         ​         ==静态== 的同步方法，同步监视器是：当前类本身即 ==类.class==

    3. ==方式三：[Lock](#4.1 Lock)==




### 4. 线程的安全问题---死锁

- 死锁的理解：不同的线程分别占用对方需要的同步资源不放弃，都在等待对方放弃自己需要的同步资源，就形成了线程的死锁.
- 如果有2个线程，2个对象。一个线程先握a🔒，再b🔒，另一个线程先握b🔒，再a🔒。很容易造成死锁。如：线程1进入a后，若sleep，造成阻塞状态，则线程2开启，若sleep，造成阻塞状态。此时线程1和线程2都不释放对方想要的资源，造成死锁。

##### 4.1 Lock

-- JDK5.0后新增

-- 建议优先使用顺序：

 \* Lock--> 同步代码块（已经进入了方法体，分配了相应资源）--> 同步方法（在方法体之外）

##### 4.2 单例设计模式

所谓类的单例设计模式，就是采取一定的方法保证在整个的软件系统中，对某个类只能存在一个对象实例。

**实现**

 饿汉式  vs 懒汉式：

|              | 好处                     | 坏处             |
| ------------ | ------------------------ | ---------------- |
| 饿汉式       | 线程安全                 | 对象加载时间过长 |
| 懒汉式       | 延迟对象的创建           | 线程不安全       |
| 改进的懒汉式 | 延迟对象的创建，线程安全 |                  |

```java
//饿汉式：
public class SingletonTest1{
public static void main(String[] args) {
	Bank bank1 = Bank.getInastance();
	Bank bank2 = Bank.getInastance();
	System.out.println(bank1 ==bank2);
}
}
class Bank{
	private Bank(){
	}
	private static Bank instance = new Bank();
	public static Bank getInastance(){
		return instance;
	}
}

//改进前的懒汉式
public class SingletonTest2 {
	public static void main(String[] args) {
		Order order1 = Order.getInstance();
		Order order2 = Order.getInstance();
		System.out.println(order1 == order2);
	}
}
class Order{
	//1.私有化类的构造器
	private Order(){
	}
	//2.声明当前类对象，没有初始化
	//4.此对象也必须声明为static的
	private static Order instance = null;
	//3.声明public、static的返回当前类对象的方法
	public static Order getInstance(){	
		if(instance == null){
			instance = new Order();
		}
		return instance;
	}
}
//使用同步机制将单例模式中的懒汉式改写为线程安全的
public class BankTest {

}
class Bank{
    private Bank(){}
    private static Bank instance = null;
    public static Bank getInstance(){
        //方式一：效率稍差
//        synchronized (Bank.class) {
//            if(instance == null){
//
//                instance = new Bank();
//            }
//            return instance;
//        }
        //方式二：效率更高
        if(instance == null){
            synchronized (Bank.class) {
                if(instance == null){
                    instance = new Bank();
                }
            }
        }
        return instance;
    }

}
```



### 5. 线程通信

* 涉及到的三个方法：

  wait():   一旦执行此方法，<u>当前线程就进入阻塞状态，并==释放==同步监视器</u>。

  notify(): 一旦执行此方法，就会唤醒被wait的一个线程。如果有多个线程被wait，就唤醒优先级高的那个。

  notifyAll(): 一旦执行此方法，就会唤醒所有被wait的线程。

- wait()，notify()，notifyAll()三个方法:
  1. 必须使用在同步代码块或同步方法中
  2. 三个方法的调用者必须是同步代码块或同步方法中的同步监视器
  3. 三个方法是定义在==java.lang.Object类==中

- 线程通信的应用：经典例题：==生产者/消费者问题==

[面试题1](#1 synchronized 与 Lock的异同？)

[面试题2](#2 sleep() 和 wait()的异同？)

## 常用类

### 1. String 类

String:字符串，使用一对""引起来表示。

- 1. String声明为<u>final</u>的，不可被继承

  2. String实现了==Serializable==接口：表示字符串是支持序列化的。

     实现了Comparable接口：表示String可以比较大小

  3. String内部定义了final char[] value用于存储字符串数据

  4. String:代表不可变的字符序列。简称：==不可变性==。

     体现：

     - - 当对字符串重新赋值时，需要重写指定内存区域赋值，不能使用原有的value进行赋值
       - 当对现有的字符串进行连接操作时，也需要重新指定内存区域赋值，不能使用原有的value进行赋值
       -  当调用String的replace()方法修改指定字符或字符串时，也需要重新指定内存区域赋值，不能使用原有的value进行赋值

  5. 通过字面量的方式（区别于new）给一个字符串赋值，此时的字符串值声明在字符串==常量池==中。

     [面试题](#1. String)

  6. 字符串常量池中是不会存储相同内容的字符串的。

  7. 常量与常量的拼接结果在常量池。且常量池中不会存在相同内容的常量。

     只要其中有一个是变量（注意如果变量有final就不是变量了），结果就在堆中。

     如果拼接的结果调用==intern()== 方法，返回值就在常量池中

  8. String中常用的==方法==

     - int length()：返回字符串的长度

     - char charAt(int index)： 返回某索引处的字符

     - boolean isEmpty()：判断是否是空字符串：return value.length == 0

     - String toLowerCase()：使用默认语言环境，将 String 中的所有字符转换为小写

     - String toUpperCase()：使用默认语言环境，将 String 中的所有字符转换为大写

     - String ==trim()==：返回字符串的副本，忽略前导空白和尾部空白

     - boolean equals(Object obj)：比较字符串的==内容==是否相同

     - boolean equalsIgnoreCase(String anotherString)：与equals方法类似，忽略大小写

     - String concat(String str)：将指定字符串连接到此字符串的结尾。 等价于用“+”

     - int compareTo(String anotherString)：比较两个字符串的大小

     - String substring(int beginIndex)：返回一个新的字符串，它是此字符串的从beginIndex开始截取到最后的一个子字符串。

     - String substring(int beginIndex, int endIndex) ：返回一个新字符串，它是此字符串从beginIndex开始截取到endIndex(不包含)的一个子字符串。

     - boolean ==endsWith==(String suffix)：测试此字符串是否以指定的后缀结束

     - boolean startsWith(String prefix)：测试此字符串是否以指定的前缀开始

     - boolean startsWith(String prefix, int toffset)：测试此字符串从指定索引开始的子字符串是否以指定前缀开始

     - boolean ==contains==(CharSequence s)：当且仅当此字符串包含指定的 char 值序列时，返回 true

     - int ==indexOf==(String str)：返回指定子字符串在此字符串中第一次出现处的索引

     - int indexOf(String str, int fromIndex)：返回指定子字符串在此字符串中第一次出现处的索引，从指定的索引开始

     - int lastIndexOf(String str)：返回指定子字符串在此字符串中最右边出现处的索引

     - int lastIndexOf(String str, int fromIndex)：返回指定子字符串在此字符串中最后一次出现处的索引，从指定的索引开始反向搜索

       注：indexOf和lastIndexOf方法如果未找到都是返回-1

     - String ==replace== (char oldChar, char newChar)：返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的<u>所有</u> oldChar 得到的。

     - String replace(CharSequence target, CharSequence replacement)：使用指定的字面值替换序列替换此字符串所有匹配字面值目标序列的子字符串。

     - String replaceAll(String regex, String replacement)：使用给定的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串

     - String replaceFirst(String regex, String replacement)：使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。

     - boolean ==matches==(String regex)：告知此字符串是否==匹配==给定的正则表达式。

     - String[] ==split==(String regex)：根据给定正则表达式的匹配拆分此字符串。

       String[] split(String regex, int limit)：根据匹配给定的正则表达式来拆分此字符串，最多不超过limit个，如果超过了，剩下的全部都放到最后一个元素中。

     - 

  9. [String 类与 char[] 的转换](#包装类的转换)

     ```java
     //String --> char[]:调用String的toCharArray()
     char[] charArray = str1.toCharArray();
     //char[] --> String:调用String的构造器
     String str2 = new String(arr);
     ```

  10. String类与Byte[] 的转换

      编码：字符串 -->字节  (看得懂 --->看不懂的二进制数据)

      解码：编码的逆过程，字节 --> 字符串 （看不懂的二进制数据 ---> 看得懂）

      说明：解码时，要求解码使用的字符集必须与编码时使用的字符集一致，否则会出现乱码。

  11. 

### 2. StringBuilder & StringBuffer

#### 2.1 String、StringBuffer、StringBuilder三者的异同？

|               | 是否可变         | 存储                 | 线程                          |
| ------------- | ---------------- | -------------------- | ----------------------------- |
| String        | 不可变的字符序列 | 底层使用 char[] 存储 |                               |
| StringBuffer  | 可变的字符序列   | 底层使用 char[] 存储 | 线程不安全的，效率高          |
| StringBuilder | 可变的字符序列   | 底层使用 char[] 存储 | jdk5.0新增,线程安全的，效率低 |

- 源码分析：

  ```java
  String str = new String();//char[] value = new char[0];
  String str1 = new String("abc");//char[] value = new char[]{'a','b','c'};
  
  StringBuffer sb1 = new StringBuffer();//char[] value = new char[16];底层创建了一个长度是16的数组。
  System.out.println(sb1.length());//
  sb1.append('a');//value[0] = 'a';
  sb1.append('b');//value[1] = 'b';
  
  StringBuffer sb2 = new StringBuffer("abc");//char[] value = new char["abc".length() + 16];
  ```

  - 问题 1

    `System.out.println(sb2.length());//3`

  - 问题 2 . 扩容问题

    如果要添加的数据底层数组盛不下了，那就需要扩容底层的数组。默认情况下，扩容为原来容量的 `2倍 + 2` ，同时将原有数组中的元素复制到新的数组中。

- - - 指导意义：开发中建议大家使用：StringBuffer(int capacity) 或 StringBuilder(int capacity)

#### 2.2 StringBuffer的常用方法

- StringBuffer append(xxx)：提供了很多的append()方法，用于进行字符串拼接
- StringBuffer delete(int start,int end)：删除指定位置的内容
- StringBuffer replace(int start, int end, String str)：把[start,end)位置替换为str
- StringBuffer insert(int offset, xxx)：在指定位置插入xxx
- StringBuffer reverse() ：把当前字符序列逆转
- public int indexOf(String str)
- public String ==substring==(int start,int end):==返回==一个从start开始到end索引结束的左闭右开区间的子字符串
- public int length()
- public char charAt(int n )
- public void setCharAt(int n ,char ch)

总结：

- 增：append(xxx)
- 删：delete(int start,int end)
- 改：setCharAt(int n ,char ch) / replace(int start, int end, String str)
- 查：charAt(int n )
- 插：insert(int offset, xxx)
- 长度：length();
- *遍历：for() + charAt() / toString()

效率：从高到低排列：StringBuilder > StringBuffer > String

### 3. 时间相关的API

##### 3.1 System.currentTimeMillis() 

```Java
long time = System.currentTimeMillis();
//返回当前时间与1970年1月1日0时0分0秒之间以毫秒为单位的时间差，称为时间戳
```

##### 3.2 Date类

java.util.Date类
​           |---java.sql.Date类

- 1. 两个构造器的使用

     > 构造器一：Date()：创建一个对应当前时间的Date对象
     >
     > 构造器二：创建指定毫秒数的Date对象2.

  2. 两个方法的使用

     > toString(): 显示当前的年、月、日、时、分、秒
     >
     > getTime():获取当前Date对象对应的毫秒数。（==时间戳== ）

  3. java.sql.Date对应着数据库中的日期类型的变量

     > 如何实例化
     >
     > 如何将java.util.Date对象转换为java.sql.Date对象

##### 3.3 SimpleDateFormat类

```java
SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");
Date date = new Date();
//格式化：日期 --->字符串
String format1 = sdf1.format(date);
System.out.println(format1);//2019-02-18 11:48:27

//解析: 字符串 ---> 日期
//要求字符串必须是符合SimpleDateFormat识别的格式(通过构造器参数体现),否则，抛异常
Date date2 = sdf1.parse("2020-02-18 11:48:27");
System.out.println(date2);
```

**java.util.Date --》 java.sql.Date**

```java
String birth = "2020-09-08";
SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd");
Date date = sdf1.parse(birth);
java.sql.Date birthDate = new java.sql.Date(date.getTime());
System.out.println(birthDate);
```

##### 3.4 Calendar 日历类

Calendar 是抽象类

- 1. 实例化

     ```java
     //方式一：创建其子类（GregorianCalendar）的对象
     //方式二：调用其静态方法getInstance()
     Calendar calendar = Calendar.getInstance();
     ```

  2. 常用方法

     - get()获取常用属性，如本月的第几天

       ```java
       Calendar calendar = Calendar.getInstance();
       calendar.set(month, day, year);
       System.out.println(calendar.get(Calendar.DAY_OF_WEEK));
       ```

     - set()

     - add()当前日期加上某天数

     - getTime()：日历类-->Date

     - setTime()：Date --> 日历类

##### 3.5 Java 8 中的API

java.time

- 1. ==LocalDate、LocalTime、LocalDateTime== （类似于Calendar）

     LocalDateTime相较于LocalDate、LocalTime，使用频率要高

     ```java
     LocalDateTime localDateTime = LocalDateTime.now();
     ```

     方法：

     - now(): 获取当前的日期、时间、日期+时间
     - of(): 设置指定的年、月、日、时、分、秒。没有偏移量
     - getXxx()：获取属性
     - withXxx()：设置属性，体现==不可变性==
     - plusXxx()：加上年月日，体现==不可变性==
     - minusXxx()：减去年月日，体现==不可变性

  2. ==Instant 瞬时==（类似于 java.util.Date类）

     ```java
     Instant instant = Instant.now();
     ```

     方法：

     - now(): 获取本初子午线对应的标准时间
     - toEpochMilli():获取自1970年1月1日0时0分0秒（UTC）开始的毫秒数  ---> Date类的getTime()
     - ofEpochMilli():通过给定的毫秒数，获取Instant实例  -->Date(long millis)

  3. ==DateTimeFormatter:格式化或解析日期、时间==（类似于SimpleDateFormat）   

### 4. Java 比较器

实现对象的排序：Comparable 或 Comparator

- ==Comparable==  自然排序

  1. 像String、包装类等实现了Comparable接口，重写了compareTo(obj)方法，给出了比较两个对象大小的方式。

  2.  像String、包装类重写compareTo()方法以后，进行了从小到大的排列

  3. 重写compareTo(obj)的规则：

     > 如果当前对象this大于形参对象obj，则返回正整数，
     >
     > 如果当前对象this小于形参对象obj，则返回负整数，
     >
     > 如果当前对象this等于形参对象obj，则返回零。​    

  4. 对于自定义类来说，如果需要排序，我们可以让自定义类实现Comparable接口，重写compareTo(obj)方法。       在compareTo(obj)方法中指明如何排序

- ==Comparator==  定制排序

  1. 背景：

     > 当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，或者实现了java.lang.Comparable接口的排序规则不适合当前的操作，那么可以考虑使用 Comparator 的对象来排序

  2. 重写compare(Object o1,Object o2)方法，比较o1和o2的大小：

     > 如果方法返回正整数，则表示o1大于o2； 
     >
     > 如果返回0，表示相等； 
     >
     > 返回负整数，表示o1小于o2。   

-  Comparable接口与Comparator的使用的==对比==：

   \*    Comparable接口的方式一旦一定，保证Comparable接口实现类的对象在任何位置都可以比较大小。

   \*    Comparator接口属于临时性的比较。

### 5. System类

### 6. Math类

### 7.BigInteger 和 BigDecimal

### 8. 枚举类

**使用：**

- 类的<u>对象只有有限个</u>，确定的。我们称此类为枚举类

- 当需要定义一组常量时，强烈建议使用枚举类
- 如果枚举类中只有一个对象，则可以作为单例模式的实现方式。

**定义：**

 * 方式一：jdk5.0之前，自定义枚举类
 * 方式二：jdk5.0，可以使用enum关键字定义枚举类

```
定义的枚举类默认继承于java.lang.Enum类
```

**Enum类中的常用方法：**

- values()方法：返回枚举类型的对象数组。该方法可以很方便地遍历所有的枚举值。

 *    valueOf(String str)：可以把一个字符串转为对应的枚举类对象。要求字符串必须是枚举类对象的“名字”。如是，会有运行时异常：IllegalArgumentException。
 *    toString()：返回当前枚举类对象常量的名称

**使用enum关键字定义的枚举类实现接口的情况**

*   情况一：实现接口，在enum类中实现抽象方法
*   情况二：让枚举类的对象分别实现接口中的抽象方法

### 9. 注解（Anotation）

Annotation 其实就是代码里的特殊标记, 这些标记可以在编译, 类加载, 运行时被读取, 并执行相应的处理。通过使用 Annotation,程序员可以在不改变原有逻辑的情况下, 在源文件中嵌入一些补充信息。

```
如何自定义注解：参照@SuppressWarnings定义
    * ① 注解声明为：@interface
    * ② 内部定义成员，通常使用value表示
    * ③ 可以指定成员的默认值，使用default定义
    * ④ 如果自定义注解没有成员，表明是一个标识作用。
```

```
如果注解有成员，在使用注解时，需要指明成员的值
自定义注解必须配上注解的信息处理流程(使用反射)才有意义。
自定义注解通过都会指明两个元注解：Retention、Target
```

- jdk 提供的4种元注解

  ==元注解== ：对现有的注解进行解释说明的注解

  - 1. **Retention**：指定所修饰的 Annotation 的生命周期：

  - - - SOURCE：在源文件中有效（保留）

      - CLASS(默认行为)：在class文件中有效

      - RUNTIME：在运行是有效

        <u>只有声明为RUNTIME生命周期的注解，才能通过反射获取</u>

  - 2. **Target:** 用于指定被修饰的 Annotation 能用于修饰哪些程序元素

    ---

    *******出现的频率较低*******

- - 3. **Documented:** 表示所修饰的注解在被javadoc解析时，保留下来
  - 4. **Inherited:** 被它修饰的 Annotation 将具有继承性

- 通过反射获取注解信息 ---到反射内容时系统讲解

- jdk 8 中注解的新特性：可重复注解、类型注解

- - - 可重复注解：

      ​      ① 在MyAnnotation上声明@Repeatable，成员值为MyAnnotations.class

      ​      ② MyAnnotation的Target和Retention等元注解与MyAnnotations相同

    - 类型注解：
      ​       ElementType.TYPE_PARAMETER 表示该注解能写在类型变量的声明语句中（如：泛型声明）
      ​       ElementType.TYPE_USE 表示该注解能写在使用类型的任何语句中

## 集合

### 1. 概述

1. 集合、数组都是对多个数据进行存储操作的结构，简称Java容器。

   此时的存储，主要指的是内存层面的存储，不涉及到持久化的存储（.txt,.jpg,.avi，数据库中）

2. 数组在存储多个数据方面的优缺点：

   特点：

   >  一旦初始化以后，其长度就确定了
   >
   > 数组一旦定义好，其元素的类型也就确定了。我们也就只能操作指定类型的数据了

   缺点：

   > 一旦初始化以后，其长度就不可修改
   >
   > 数组中提供的方法非常有限，对于添加、删除、插入数据等操作，非常不便，同时效率不高
   >
   > 获取数组中实际元素的个数的需求，数组没有现成的属性或方法可用
   >
   > 数组存储数据的特点：有序、可重复。对于无序、不可重复的需求，不能满足

3. 集合框架

   > ----==Collection==接口：单列集合，用来存储一个一个的对象
   >
   > > ----List接口：==存储有序的、可重复的数据==。  -->“动态”数组
   > >
   > > > ----ArrayList、LinkedList、Vector
   > >
   > > ----Set接口：==存储无序的、不可重复的数据==   -->高中讲的“集合”
   > >
   > > >  ----HashSet、LinkedHashSet、TreeSet
   > > >
   > > >
   >
   > ----==Map==接口：双列集合，用来存储一对(key(相当于x) - value(相当于y))一对的数据   -->高中函数：==y = f(x)==
   >
   > > ----HashMap、LinkedHashMap、TreeMap、Hashtable、Properties
   > >
   > >

   ```mermaid
   graph TD
   	List --> collection
   	Set --> collection
   	
   	Vector -.-> List
   	ArrayList -.-> List
   	LinkList -.-> List
   	
   	HashSet -.-> Set
   	LinkedHashSet --> HashSet
   	
   	SortedSet --> Set
   	TreeSet -.-> SortedSet
   ```

### 2. Collection接口常用方法

向Collection接口的实现类的对象中添加数据obj时，==要求obj所在类要重写equals()==

注：<u>一旦用Collection创建类，则对集合的添加或者删除元素都是在一个大的全集里操作的</u>

```java
//创建全集
Collection coll = new ArrayList();
//创建子集
Collection coll1 = Arrays.asList(123,456,789);
```

- 1. ==contains==(Object obj):判断当前集合中是否包含obj，在判断时会调用obj对象所在类的equals()

  2. containsAll(Collection coll1):判断形参coll1中的所有元素是否都存在于当前集合中

  3. ==remove==(Object obj):从当前集合中移除obj元素

  4. removeAll(Collection coll1):**差集**：从当前集合中移除coll1中所有的元素（全集U - coll1）

  5. ==retainAll==(Collection coll1):**交集**：获取当前集合和coll1集合的交集，并返回给当前集合

  6. equals(Object obj): 要想返回true，需要当前集合和形参集合的元素及其<u>顺序</u>都相同。

  7. ==hashCode==(): 返回当前对象的哈希值

  8. toArray(): 集合 --->数组 

     ```java
     Object[] arr = coll.toArray();
     ```

  9. 数组 --->集合:调用Arrays类的静态方法asList()

     ```java
     List<String> list = Arrays.asList(new String[]{"AA", "BB", "CC"});
     ```

  10. ==iterator()==:返回Iterator接口的实例，用于遍历集合元素。放在IteratorTest.java中测试

      > ---- hasNext() : 判断是否还有下一个元素
      >
      > ---- next()：①指针下移 ②将下移以后集合位置上的元素返回
      >
      >

      ```java
      ArrayList list = new ArrayList();
      Iterator iterator = list.iterator();
      while(iterator.hasNext()){
          System.out.println(iterator.next());
      }
      ```

      注：集合对象<u>每次调用iterator()方法都得到一个全新的迭代器对象</u>，默认游标都在集合的<u>第一个元素之==前==</u>。

  11. ==foreach()==：jdk 5.0 新增，用于遍历集合、数组

      ```java
      //for(集合元素的类型 局部变量 : 集合对象),内部仍然调用了迭代器。
      for(Object obj : coll){
          System.out.println(obj);
      }
      ```

### 3. Collection 子接口

#### 3.1 List（有序的）

[面试题：ArrayList、LinkedList、Vector三者的异同](#1. ArrayList、LinkedList、Vector三者的异同？)

##### 3.1.1 ArrayList的源码分析：

**jdk 7情况下：**

```java
ArrayList list = new ArrayList();//底层创建了长度是10的Object[]数组elementData
list.add(123);//elementData[0] = new Integer(123);
...
list.add(11);//如果此次的添加导致底层elementData数组容量不够，则扩容。
```

​    默认情况下，扩容为原来的容量的==1.5倍==，同时需要将原有数组中的数据复制到新的数组中

**jdk 8中ArrayList的变化:**

```java
 ArrayList list = new ArrayList();//底层Object[] elementData初始化为{}.并没有创建长度为10的数组
 list.add(123);//第一次调用add()时，底层才创建了长度10的数组，并将数据123添加到elementData[0]
...
//后续的添加和扩容操作与jdk 7 无异。
```

**小结**：

​	jdk7中的ArrayList的对象的创建类似于单例的==饿汉式==，而jdk8中的ArrayList的对象的创建类似于单例的==懒汉式==，延迟了数组的创建，节省内存

##### 3.1.2 LinkedList的源码分析

```java
LinkedList list = new LinkedList(); //内部声明了Node类型的first和last属性，默认值为null
list.add(123);//将123封装到Node中，创建了Node对象
```

其中，Node定义为：

```java
private static class Node<E> {
     E item;
     Node<E> next;
     Node<E> prev;//体现了LinkedList的双向链表的说法
     Node(Node<E> prev, E element, Node<E> next) {
     this.item = element;
     this.next = next;
     this.prev = prev;
	}
}
```

##### 3.1.3 Vector的源码分析

jdk7和jdk8中通过Vector()构造器创建对象时，底层都创建了长度为10的数组。在扩容方面，默认扩容为原来的数组长度的==2倍==。

#### 3.2 LinkedList 

##### 3.2.1 List接口中的常用方法

- void add(int index, Object ele)：在index位置插入ele元素

- boolean addAll(int index, Collection eles)：从index位置开始将eles中的所有元素添加进来

- Object get(int index)：获取指定index位置的元素

- int ==indexOf==(Object obj)：返回obj在集合中首次出现的位置

- int lastIndexOf(Object obj)：返回obj在当前集合中末次出现的位置

- Object ==remove==(int index)：移除指定<u>index位置的元素</u>（不是删除对象，即区分Collection中的remove(Object obj)），并返回此元素

  ```java
  list.remove(2);//移除指定索引2处的元素
  list.remove(new Integer(2));//从当前集合中移除obj元素
  ```

- Object set(int index, Object ele)：设置指定index位置的元素为ele

- List subList(int fromIndex, int toIndex)：返回从 [fromIndex,oIndex) 位置的子集合

**总结常用方法：**

- 增：add(Object obj)

- 删：remove(int index) / remove(Object obj)

- 改：set(int index, Object ele)

- 查：get(int index)

- 插：add(int index, Object ele)

- 长度：size()

- 遍历：

  ​     ① Iterator迭代器方式
  ​     ② 增强for循环
  ​     ③ 普通的循环

#### 3.3 Set

##### 1. Set 接口的框架

> ----Collection接口：单列集合，用来存储一个一个的对象
>
> >----Set接口：存储无序的、不可重复的数据   -->高中讲的“集合”
> >
> >>----HashSet：作为Set接口的主要实现类；线程不安全的；可以存储null值
> >>
> >>>----LinkedHashSet：作为HashSet的子类；遍历其内部数据时，可以按照添加的顺序遍历对于频繁的遍历操作，LinkedHashSet效率高于HashSet
> >>
> >>----TreeSet：可以按照添加对象的指定属性，进行排序
> >
> >

注：

1. <u>Set接口中没有额外定义新的方法</u>，使用的都是Collection中声明过的方法。因为无序，不需要索引。
2. 要求：
   - 向Set(主要指：HashSet、LinkedHashSet)中添加的数据，其所在的类一定要==重写hashCode()和equals()==
   - 重写的hashCode()和equals()尽可能保持一致性：相等的对象必须具有相等的散列码

3. 重写两个方法的小技巧：对象中用作 equals() 方法比较的 Field，都应该用来计算 hashCode 值。


##### 2. Set：存储无序的、不可重复的数据--以HashSet为例

        1. 无序性：不等于随机性。存储的数据在底层数组中并非按照数组索引的顺序添加，而是数据的==哈希值==决定的。无序性是相对于List的有序（根据添加的顺序）来说的。
        2. 不可重复性：保证添加的元素按照equals()判断时，不能返回true.即：相同的元素只能添加一个。

##### 3. 添加元素的过程----以HashSet为例

​    我们向HashSet中添加元素a，首先调用元素a所在类的hashCode()方法，计算元素a的哈希值，此哈希值接着通过某种算法计算出在HashSet底层数组中的存放位置（即为：索引位置），判断数组此位置上是否已经有元素：

> 如果此位置上没有其他元素，则元素a添加成功。 ---> ==情况1==
>
> 如果此位置上有其他元素b(或以链表形式存在的多个元素），则比较元素a与元素b的hash值：
>
> >  如果hash值不相同，则元素a添加成功。---> ==情况2==
> >  如果hash值相同，进而需要调用元素a所在类的equals()方法：
> >
> > > equals()返回true，元素a添加失败
> > > equals()返回false，则元素a添加成功。---> ==情况2==



对于添加成功的情况 2 和情况 3 而言：元素a 与已经存在指定索引位置上数据以==链表==的方式存储。
jdk 7 :元素 a 放到数组中，指向原来的元素。
jdk 8 :原来的元素在数组中，指向元素 a
总结：七上八下

==HashSet底层：数组+链表的结构==

( 数字表示commer来的顺序 )

```mermaid
graph TD
	subgraph JDK8
	jdk8_commer4-->jdk8_commer3
	jdk8_commer3-->jdk8_commer2
	jdk8_commer2-->jdk8_commer1
	end
	
	subgraph JDK7
	jdk7_commer1-->jdk7_commer2
	jdk7_commer2-->jdk7_commer3
	jdk7_commer3-->jdk7_commer4
	end
```

##### 4.  LinkedHashSet

- LinkedHashSet作为HashSet的子类，在添加数据的同时，每个数据还维护了两个引用，记录此数据前一个
  ​    数据和后一个数据。
- 优点：对于频繁的遍历操作，LinkedHashSet效率高于HashSet

##### 5. TreeSet

可以按照添加对象的指定属性，进行排序

1. 向TreeSet中添加的数据，要求是相同类的对象。
2. 两种排序方式：自然排序（实现Comparable接口） 和 定制排序（Comparator）
3. 自然排序中，比较两个对象是否相同的标准为：==compareTo==()返回0.不再是equals()
4. 定制排序中，比较两个对象是否相同的标准为：compare()返回0.不再是equals()

### 4. Map

#### 4.1. Map的实现类的结构：

 *  > **Map**:双列数据，存储key-value对的数据   ---类似于高中的函数：y = f(x)
   >
   > > 1. **HashMap**：作为Map的主要实现类；线程不安全的，效率高；==存储null的key和value==
   > >
   > >    > **LinkedHashMap**：保证在遍历map元素时，可以按照添加的顺序实现遍历。
   > >    >
   > >    > 原因：在原有的HashMap底层结构基础上，添加了一对指针，指向前一个和后一个元素。
   > >    >
   > >    > 对于频繁的遍历操作，此类执行效率高于HashMap
   > >
   > > 2. **TreeMap**：保证按照添加的key-value对进行排序，实现排序遍历。此时考虑key的<u>自然排序或定制排序</u>底层使用==红黑树==
   > >
   > > 3. **Hashtable**：作为古老的实现类；线程安全的，效率低；不能存储null的key和value
   > >
   > >    > **Properties**：常用来处理配置文件。key和value都是String类型



```mermaid
graph LR
	
	subgraph Set
	subgraph KeySet--Set
	AA
	BB
	CC
	DD 
	end
	
	
	subgraph Values--Collection
	90
	90
	56
	78
	end
	end
	
	AA --> 90
	BB --> 90
	CC --> 56
	DD --> 78
	
	4个Entry --> AA
	4个Entry --> BB
	4个Entry --> CC
	4个Entry --> DD

```

遍历：

```java
//遍历key
Set<String> keySet = map.keySet()；
for(String key:keySet){
	System.out.println(key);
}
//遍历value
Collection<Integer> values = map.values();
Iterator<Integer> iterator = values.iterator();
while (iterator.hasNext()){
    System.out.println(iterator.next());
}
//遍历Entry
Set<Map .Entry<String,Integer>> entrySet =  map.entrySet();
Iterator<Map.Entry<String,Integer>> iterator = entrySet.iterator();
while (iterator.hasNext()){
    Map.Entry<String ,Integer> entry = iterator.next();
    System.out.println(entry.getKey() + entry.getValue());
}
```



HashMap的底层：

1. 数组+链表  （jdk7及之前）
2. 数组+链表+红黑树 （jdk 8）

[面试题2](#2. Map)

#### 4.2. Map结构的理解：

1. Map中的 ==key==：无序的、不可重复的，使用==Set存储==所有的key ==> key所在的类要重写equals()和hashCode() （以HashMap为例）
2. Map中的 ==value== ：无序的、可重复的，使用==Collection存储==所有的value   ==> value所在的类要重写equals()
3. 一个键值对（==Entry对象==）：key-value构成了一个Entry对象。Map中的entry:无序的、不可重复的，使用Set存储所有的entry

#### 4.3 HashMap的底层实现原理？以jdk7为例说明：

```java
HashMap map = new HashMap();
//在实例化以后，底层创建了长度是16的一维数组Entry[] table
//...可能已经执行过多次put...
map.put(key1,value1);
```

1. put操作以后：

   首先，调用key1所在类的hashCode()计算key1哈希值，此哈希值经过某种算法计算以后，得到在Entry数组中的存放位置。

   > 如果此位置上的数据为空，此时的key1-value1添加成功。 ----==情况1==
   >
   > 如果此位置上的数据不为空，(意味着此位置上存在一个或多个数据(以链表形式存在))，比较key1和已经存在的一个或多个数据的哈希值：
   >
   > > 如果key1的哈希值与已经存在的数据的<u>哈希值都不相同</u>，此时key1-value1添加成功。----==情况2==
   > >
   > > 如果key1的哈希值和已经存在的某一个数据(key2-value2)的<u>哈希值相同</u>，继续比较：调用key1所在类的equals(key2)方法，比较：
   > >
   > > > 如果equals()返回false：此时key1-value1添加成功。----==情况3==
   > > >
   > > > 如果equals()返回true：使用value1替换value2（==修改==功能）

   补充：关于情况2和情况3：此时key1-value1和原来的数据以链表的方式存储

   在不断的添加过程中，会涉及到扩容问题，当超出临界值(且要存放的位置非空)时，扩容。默认的扩容方式：扩容为原来容量的2倍，并将原有的数据复制过来。

2. jdk8 相较于jdk7在底层实现方面的不同：

   - 1. new HashMap():底层没有创建一个长度为16的数组
     2. jdk 8底层的数组是：==Node[]==,而非Entry[]
     3. 首次调用==put()方法时，底层创建长度为16的数组==
     4. jdk7底层结构只有：数组+链表。jdk8中底层结构：数组+链表+红黑树。

     1. > 4.1 形成链表时，七上八下（jdk7:新的元素指向旧的元素。jdk8：旧的元素指向新的元素）.
        >
        > 4.2 当数组的某一个索引位置上的元素以链表形式存在的数据个数 > 8 且当前数组的长度 > 64时，此时此索引位置上的所数据改为使用红黑树存储。
        >
        > - DEFAULT_INITIAL_CAPACITY : HashMap的默认容量，16
        > - DEFAULT_LOAD_FACTOR：HashMap的==默认加载因子==：0.75
        > - threshold：==扩容的临界值==，=容量*填充因子：16 * 0.75 => 12
        > - TREEIFY_THRESHOLD：Bucket中链表长度大于该默认值，转化为红黑树:8
        > - MIN_TREEIFY_CAPACITY：桶中的Node被树化时最小的hash表容量:64

#### 4.4 LinkedHashMap的底层实现原理（了解）

 ```java
//源码中：
static class Entry<K,V> extends HashMap.Node<K,V> {
     Entry<K,V> before, after;//能够记录添加的元素的先后顺序
     Entry(int hash, K key, V value, Node<K,V> next) {
        super(hash, key, value, next);
     }
 }
 ```

#### 4.5 Map中定义的方法

1. 添加、删除、修改操作：
   - Object put(Object key,Object value)：将指定key-value添加到(或==修改==)当前map对象中
   - void putAll(Map m):将m中的所有key-value对存放到当前map中
   - Object remove(Object key)：移除指定key的key-value对，并返回value
   - void clear()：清空当前map中的所有==数据==，不是让对象等于null
2.  元素查询的操作
   - Object get(Object key)：获取指定key对应的value
   - boolean containsKey(Object key)：是否包含指定的key
   -  boolean containsValue(Object value)：是否包含指定的value
   -  int size()：返回map中key-value对的个数
   -  boolean isEmpty()：判断当前map是否为空
   -  boolean equals(Object obj)：判断当前map和参数==对象obj==是否相等
3. 元视图操作的方法：
   - Set ==keySet==()：返回所有key构成的Set集合
   -  Collection ==values==()：返回所有value构成的Collection集合
   -  Set ==entrySet==()：返回所有key-value对构成的Set集合 

 **总结**：常用方法：
 * 添加：put(Object key,Object value)
 * 删除：remove(Object key)
 * 修改：put(Object key,Object value)
 * 查询：get(Object key)
 * 长度：size()
 * 遍历：keySet() / values() / entrySet()

#### 4.6 TreeMap

向TreeMap中添加key-value，要求key必须是由同一个类创建的对象。因为要<u>按照key进行排序</u>：自然排序 、定制排序

#### 4.7 Hashtable-----Properties

Properties：常用来处理配置文件。key和value都是String类型

#### 4.8 Collections工具类

[面试题](#3. Collection和Collections的区别)

Collections：操作Collection、Map的工具类

常用方法：

- reverse(List)：反转 List 中元素的顺序

- shuffle(List)：对 List 集合元素进行随机排序

- sort(List)：根据元素的自然顺序对指定 List 集合元素按升序排序

- sort(List，Comparator)：根据指定的 Comparator 产生的顺序对 List 集合元素进行排序

- swap(List，int， int)：将指定 list 集合中的 i 处元素和 j 处元素进行交换

- Object max(Collection)：根据元素的自然顺序，返回给定集合中的最大元素

- Object max(Collection，Comparator)：根据 Comparator 指定的顺序，返回给定集合中的最大元素

- Object min(Collection)

- Object min(Collection，Comparator)

- int frequency(Collection，Object)：返回指定集合中指定元素的出现次数

- void copy(List dest,List src)：将src中的内容复制到dest中

  ​                  注：区分add了几个，和数组的长度（list.size）

- boolean replaceAll(List list，Object oldVal，Object newVal)：使用新值替换 List 对象的所有旧值

## 泛型

### 1.泛型的使用

```java
//泛型的嵌套
Set<Map.Entry<String,Integer>> entry = map.entrySet();
Iterator<Map.Entry<String, Integer>> iterator = entry.iterator();
```

==Map.Entry，其实Entry是Map的内部类==

1. jdk 5.0新增的特性
2. 在集合中使用泛型：

① 集合接口或集合类在jdk5.0时都修改成了带泛型的结构

② ==在实例化集合类时，可以指明具体的泛型类型==

③ 指明完以后，在集合==类==或==接口==中凡是定义类或接口时，内部结构（比如：方法、构造器、属性等）使用到类的

​      泛型的位置，都指定为实例化的泛型类型。

​      比如：add(E e)  --->实例化以后：add(Integer e)

④ 注意点：<u>泛型的类型必须是类</u>，不能是基本数据类型。需要用到基本数据类型的位置，拿包装类替换

⑤ 如果实例化时，没有指明泛型的类型。默认类型为java.lang.Object类型。

3. 如何自定义泛型结构：泛型类、泛型接口；泛型方法。见 GenericTest1.java
4. 如果定义了泛型类，实例化没有指明类的泛型，则认为此泛型类型为Object类型
   要求：如果大家定义了类是带泛型的，建议在实例化时要指明类的泛型
5. 由于子类在继承带泛型的父类时，指明了泛型类型。则实例化子类对象时，不再需要指明泛型。
6. 泛型不同的引用不能相互赋值
7. 静态方法中不能使用泛型
8. 异常类不能申明为泛型



- 泛型在继承方面的体现

虽然类A是类B的父类，但是G<A> 和G<B>二者不具备子父类关系，二者是并列关系。

 补充：类A是类B的父类，A<G> 是 B<G> 的父类

- 通配符的使用


2. 通配符的使用
   ​    通配符：?

       类A是类B的父类，G<A>和G<B>是没有关系的，二者共同的父类是：G<?>

- 添加(写入)：对于List<?>就不能向其内部添加数据，除了添加 null 之外。
- 获取(读取)：允许读取数据，读取的数据类型为Object

3. 有限制条件的通配符的使用

   ```java
   ? extends A:
          G<? extends A> 可以作为G<A>和G<B>的父类，其中B是A的子类
          （-∞，A]
   ? super A:
          G<? super A> 可以作为G<A>和G<B>的父类，其中B是A的父类
          [A,+∞)
   ```

4. ​        


## IO 流

### File类的使用

1.  File类的一个对象，代表一个文件或一个文件目录(俗称：文件夹)

2. File类声明在java.io包下

3. File类中涉及到关于文件或文件目录的创建、删除、重命名、修改时间、文件大小等方法，并未涉及到写入或读取文件内容的操作。<u>如果需要读取或写入文件内容，必须使用IO流来完成</u>

4. 后续File类的对象常会作为参数传递到流的构造器中，指明读取或写入的"终点"

5. 如何创建File类的实例

          ```java
      File(String filePath)
      File(String parentPath,String childPath)
      File(File parentFile,String childPath)
      ​    ```

6. File 常用方法

   ```java
   public String getAbsolutePath()：获取绝对路径
   public String getPath() ：获取路径
   public String getName() ：获取名称
   public String getParent()：获取上层文件目录路径。若无，返回null
   public long length() ：获取文件长度（即：字节数）。不能获取目录的长度。
   public long lastModified() ：获取最后一次的修改时间，毫秒值
   
   如下的两个方法适用于文件目录：
   public String[] list() ：获取指定目录下的所有文件或者文件目录的名称数组
   public File[] listFiles() ：获取指定目录下的所有文件或者文件目录的File数组
   ```

   - public boolean renameTo(File dest):把文件重命名为指定的文件路径
     ​     比如：file1.renameTo(file2)为例：
     ​    要想保证返回true,需要file1在硬盘中是存在的，且file2不能在硬盘中存在

7. File 类的判断功能

   ```java
   public boolean isDirectory()：判断是否是文件目录
   public boolean isFile() ：判断是否是文件
   public boolean exists() ：判断是否存在
   public boolean canRead() ：判断是否可读
   public boolean canWrite() ：判断是否可写
   public boolean isHidden() ：判断是否隐藏
   ```

8. 创建硬盘中对应的文件或文件目录

   - public boolean ==createNewFile()== ：创建文件。若文件存在，则不创建，返回false。区别于new File

   - public boolean mkdir() ：创建文件目录。如果此文件目录存在，就不创建了。如果此文件目录的<u>上层目录不存在</u>，也不创建。

   - public boolean mkdirs() ：创建文件目录。如果此文件目录存在，就不创建了。如果上层文件目录不存在，一并创建

   - 删除磁盘中的文件或文件目录

     public boolean delete()：删除文件或者文件夹
     ​    删除注意事项：Java中的删除不走回收站。

### I/O流的体系结构

#### 1. 流的分类

- 操作数据单位：字节流、字符流
- 数据的流向：输入流、输出流
- 流的角色：节点流、处理流

#### 2. 流的体系结构

|      | 抽象基类     | 节点流（或文件流）                            | 缓冲流（处理流的一种）                                     |
| ---- | ------------ | --------------------------------------------- | :--------------------------------------------------------- |
| 字节 | InputStream  | FileInputStream   (read(byte[] buffer))       | BufferedInputStream (read(byte[] buffer))                  |
| 流   | OutputStream | FileOutputStream  (write(byte[] buffer,0,len) | BufferedOutputStream (write(byte[] buffer,0,len) / flush() |
| 字符 | Reader       | FileReader (read(char[] cbuf))                | BufferedReader (read(char[] cbuf) / readLine())            |
| 流   | Writer       | FileWriter (write(char[] cbuf,0,len)          | BufferedWriter (write(char[] cbuf,0,len) / flush()         |

##### 2.1 抽象基类

**读入**

说明点：

    1. read()的理解：返回读入的一个字符。如果达到文件末尾，返回 -1
    
       ```java
       //1.实例化File类的对象，指明要操作的文件
       File file = new File("hello.txt");//相较于当前Module
       //2.提供具体的流
       FileReaderfr = new FileReader(file);
       //3.数据的读入
       int data;
       while((data = fr.read()) != -1){
       	System.out.print((char)data);
           //fr.read()一个一个的读，想要多个读入，可以带参，如fr.read(char[])
       }
       //4.流的关闭操作
       if(fr != null){
           try {
               fr.close();
           } catch (IOException e) {
               e.printStackTrace();
           }
       }
       ```
    
    2. 异常的处理：为了保证流资源一定可以执行关闭操作。需要使用try-catch-finally处理
    
    3. 读入的文件一定要存在，否则就会报FileNotFoundException。

**写出**

从内存中写出数据到硬盘的文件里。

```java
//1.提供File类的对象，指明写出到的文件
File file = new File("hello1.txt");
//2.提供FileWriter的对象，用于数据的写出
fw = new FileWriter(file,false);
//3.写出的操作
fw.write("I have a dream!\n");
```

说明：

1. 输出操作，对应的 ==File可以不存在==的。并不会报异常

2. > File对应的硬盘中的文件如果不存在，在输出的过程中，会自动创建此文件。
   > File对应的硬盘中的文件如果存在：
   >
   > > 如果流使用的构造器是：FileWriter(file,==false==) / FileWriter(file):对原有文件的==覆盖==
   > >
   > > 如果流使用的构造器是：FileWriter(file,==true==):不会对原有文件覆盖，而是在原有文件基础上==追加==内容​     



##### 2. 节点流/文件流

**FileInputStream和FileOutputStream的使用**

 * 结论：
 * 1. 对于文本文件(.txt,.java,.c,.cpp)，使用==字符流==处理
 * 2. 对于非文本文件(.jpg,.mp3,.mp4,.avi,.doc,.ppt,...)，使用==字节流==处理

##### 3. 缓冲流

 1.  缓冲流：

     * BufferedInputStream
     * BufferedOutputStream
     * BufferedReader
     * BufferedWriter

 2.  作用：提供流的读取、写入的速度

     提高读写速度的原因：内部提供了一个缓冲区

 3.  ==处理流==，就是“套接”在已有的流的基础上

##### 4. 转换流

```mermaid
graph LR
	Utf8.txt --字节流--> InputStreamReadrer/utf-8
	InputStreamReadrer/utf-8 --字符流-->程序
	程序 --字符流--> OutputStreamWriter/gbk
	OutputStreamWriter/gbk --字节流-->gbk.txt
```

处理流之二：转换流的使用
1. 转换流：属于==字符流==

   - InputStreamReader：将一个字节的输入流转换为字符的输入流
   - OutputStreamWriter：将一个字符的输出流转换为字节的输出流

2. 作用：提供字节流与字符流之间的转换

3. 解码：字节、字节数组  --->字符数组、字符串

   编码：字符数组、字符串 ---> 字节、字节数组

4. 字符集

   - ASCII：美国标准信息交换码。

     > 用一个字节的7位可以表示。

   -  ISO8859-1：拉丁码表。欧洲码表

     > 用一个字节的8位表示。

   - GB2312：中国的中文编码表

     > 最多两个字节编码所有字符

   - GBK：中国的中文编码表升级，融合了更多的中文文字符号

     > 最多两个字节编码

   -  Unicode：国际标准码，融合了目前人类使用的所有字符。

     > 为每个字符分配唯一的字符码。所有的文字都用两个字节来表示。

   -  UTF-8：变长的编码方式，可用1-4个字节来表示一个字符。

##### 5. 其它流

**标准的输入、输出流**

1.1

> System.in:标准的输入流，默认从键盘输入
> System.out:标准的输出流，默认从控制台输出  

1.2

> System类的setIn(InputStream is) / setOut(PrintStream ps)方式重新指定输入和输出的流。

1.3 练习：

> 从键盘输入字符串，要求将读取到的整行字符串转成大写输出。然后继续进行输入操作，
> 直至当输入“e”或者“exit”时，退出程序。

>  方法一：使用Scanner实现，调用next()返回一个字符串
> 方法二：使用System.in实现。System.in  --->  转换流 ---> BufferedReader的readLine()



**打印流：PrintStream 和PrintWriter**

2.1 提供了一系列重载的print() 和 println()
2.2 练习：

**数据流**
3.1  DataInputStream 和 DataOutputStream
3.2 作用：用于读取或写出基本数据类型的变量或字符串

练习：将内存中的字符串、基本数据类型的变量写出到文件中。

注意：处理异常的话，仍然应该使用try-catch-finally.

**对象流**

1. 序列化与反序列化

对象流的使用

- 1. ObjectInputStream 和 ObjectOutputStream

  2. 作用：用于存储和读取基本数据类型数据或对象的处理流。它的强大之处就是可以把Java中的对象写入到数据源中，也能把对象从数据源中还原回来。

  3. 要想一个java对象是可序列化的，需要满足相应的要求。见Person.java

  4. 序列化机制：

     对象序列化机制允许把内存中的Java对象转换成平台无关的二进制流，从而允许把这种二进制流持久地保存在磁盘上，或通过网络将这种二进制流传输到另一个网络节点。

  当其它程序获取了这种二进制流，就可以恢复成原来的Java对象。


==序列化== 过程：将内存中的java对象保存到磁盘中或通过网络传输出去，使用==ObjectOutputStream==实现

==反序列== 化：将磁盘文件中的对象还原为内存中的一个java对象，使用  ==ObjectInputStream== 来实现



满足如下的要求，方==可序列化==

- 1.需要实现接口：==Serializable==
- 2.当前类提供一个全局常量：serialVersionUID
- 3.除了当前Person类需要实现Serializable接口之外，还必须保证其内部所有属性
- 也必须是可序列化的。（默认情况下，基本数据类型可序列化）
- 补充：ObjectOutputStream和ObjectInputStream不能序列化static和transient修饰的成员变量


**RandomAccessFile**类

RandomAccessFile的使用

- 1. RandomAccessFile直接继承于java.lang.Object类，实现了DataInput和DataOutput接口
- 1. RandomAccessFile<u>既可以作为一个输入流，又可以作为一个输出流</u>
- 1. 如果RandomAccessFile作为输出流时，写出到的文件如果不存在，则在执行过程中自动创建。如果写出到的文件存在，则会对原有文件内容进行覆盖。（默认情况下，从头覆盖）
- 1. 可以通过相关的操作，实现RandomAccessFile“插入”数据的效果

## 网络编程

### InetAddress

一、网络编程中有两个主要的问题：

- 1. 如何准确地定位网络上一台或多台主机；定位主机上的特定的应用
  2. 找到主机后如何可靠高效地进行数据传输

二、网络编程中的两个要素：

- 1. 对应问题一：IP和端口号
  2. 对应问题二：提供网络通信协议：TCP/IP参考模型（应用层、传输层、网络层、物理+数据链路层）

三、通信要素一：IP和端口号

```mermaid
graph LR
	域名  --发给DNS解析--> DNS
    DNS --解析出地址--> IP地址
    IP地址 --在本地hosts中找对应域名地址--> hosts
    IP地址 --若hosts中没有/发给网络服务器找--> 网络服务器
    
```



 * 1. ==IP==: 唯一的标识 Internet 上的计算机（通信实体）
 * 2. 在Java中使用 ==InetAddress== 类代表IP
 * 3. ==IP分类== ：IPv4 和 IPv6 ; 万维网 和 局域网
 * 4. 域名(IP难记 于是有了域名):   www.baidu.com   www.mi.com  www.sina.com  www.jd.com www.vip.com
 * 5. ==本地回路地址==：==127.0.0.1 对应着：localhost==
 * 6. 如何实例化InetAddress:两个方法：getByName(String host) 、 getLocalHost()

       两个常用方法：getHostName() / getHostAddress()
  
 * 7. 端口号：==正在计算机上运行的进程==

       要求：不同的进程有不同的端口号

       范围：被规定为一个 16 位的整数 0~65535。
 * 8. 端口号与IP地址的组合得出一个==网络套接字：Socket==

### TCP网络协议编程

### UDP网络协议编程

代码：Java Senior day10,java1

### URL编程

 * 1. URL:统一资源定位符，对应着互联网的某一资源地址
 * 2. 格式：

      http://localhost:8080/examples/beauty.jpg?username=Tom

      协议   主机名    端口号  资源地址           参数列表

      ```java
      URL url = new URL("http://localhost:8080/examples/beauty.jpg?username=Tom");
      ```

- 3. 常用方法

     ```java
     public String getProtocol()     获取该URL的协议名
     public String getHost()         获取该URL的主机名
     public String getPort()         获取该URL的端口号
     public String getPath()         获取该URL的文件路径
     public String getFile()         获取该URL的文件名
     public String getQuery()        获取该URL的查询名
     ```



## 反射

### 疑问

1. 通过直接new的方式或反射的方式都可以调用公共的结构，开发中到底用那个？
   建议：直接new的方式。

   什么时候会使用反射的方式：当不确定对象是谁的时候。比如注册、登录时，发送注册信息，服务器跑起来，再去造相应的对象。

    ==反射的特征：动态性==。

2. 反射机制与面向对象中的封装性是不是矛盾的？如何看待两个技术？
   不矛盾。封装性是建议你调不调内部的私有或公有属性和方法，而反射机制是能不能调的问题

### 关于java.lang.Class类的理解

1. 类的加载过程：
   程序经过javac.exe命令以后，会生成一个或多个字节码文件(.class结尾)。
   接着我们使用java.exe命令对某个字节码文件(==含有main方法的class文件== )进行解释运行。相当于将某个字节码文件加载到内存中。此过程就称为==类的加载== 。<u>加载到内存中的类，我们就称为==运行时类==，此时运行时类，就作为Class 的一个实例</u>。

   ```java
   万事万物皆对象？对象.xxx,File,URL,反射,前端、数据库操作
   ```

2. 换句话说，Class的实例就对应着一个运行时类。
3. 加载到内存中的运行时类，会缓存一定的时间。在此时间之内，我们可以通过不同的方式来获取此运行时类。

### 创建运行时类的对象

通过发射创建对应的运行时类的对象

newInstance():调用此方法，创建对应的运行时类的对象。内部调用了运行时类的空参的构造器。

要想此方法正常的创建运行时类的对象，要求：
​        1. 运行时类必须==提供空参的构造器==
​        2. 空参的构造器的访问权限得够。通常，设置为public。

 在javabean中要求提供一个public的空参构造器。原因：
​    1.便于通过反射，创建运行时类的对象
​    2.便于子类继承此运行时类时，默认调用super()时，保证父类有此构造器

#### 创建运行时类的对象的方式

```java
//1.调用运行时类本身的.class属性
Class clazz1 = Person.class;
//2.通过运行时类的对象获取
Person p = new Person();
Class clazz2 = p.getClass();
//3.通过Class的静态方法获取
String className = "com.test.Person";
Class clazz3 = Class.forName(className);
//    clazz3.newInstance();//Deprecated
//4.通过类的加载器
ClassLoader classLoader = this.getClass().getClassLoader();
Class clazz4 = classLoader.loadClass(className);
System.out.println(clazz1 == clazz4); //true 即只加载一次
System.out.println(clazz2 == clazz3); //true
```

#### 获取运行时类的属性

- getFields():获取当前运行时类及其父类中声明为public访问权限的属性

- getDeclaredFields():获取当前运行时类中声明的所有属性。（不包含父类中声明的属性）

  可以用foreach语句遍历属性

#### 获取运行时类的方法结构

-  getMethods():获取当前运行时类及其所有父类中声明为public权限的方法

- getDeclaredMethods():获取当前运行时类中声明的所有方法。（不包含父类中声明的方法）

  可以用foreach语句遍历方法

#### 获取运行时类的方法的内部结构

方法的内部结构：

```java
@Xxxx
权限修饰符  返回值类型  方法名(参数类型1 形参名1,...) throws XxxException{}
```

```java
//1.获取方法声明的注解
Annotation[] annos = m.getAnnotations();
//2.权限修饰符
 System.out.print(Modifier.toString(m.getModifiers()) + "\t");
//3.返回值类型
System.out.print(m.getReturnType().getName() + "\t");
//4.方法名
System.out.print(m.getName());
System.out.print("(");
//5.形参列表
Class[] parameterTypes = m.getParameterTypes();
```

##### 其它

获取运行时类实现的接口

- getConstructors():获取当前运行时类中声明为public的构造器
- getDeclaredConstructors():获取当前运行时类中声明的所有的构造器
- getSuperclass()获取运行时类的父类
- getGenericSuperclass() 获取运行时类的带泛型的父类
- getInterfaces() 获取运行时类实现的接口
- getPackage() 获取运行时类所在的包
- getAnnotations 获取运行时类声明的注解

##### 调用运行时类中==指定==的结构：属性、方法、构造器

- getDeclaredField(String fieldName):获取运行时类中指定变量名的==属性==

  ```java
  //获取运行时类中指定变量名的属性
  Field name = clazz.getDeclaredField("name");
  //保证当前属性是可访问的
  name.setAccessible(true);
  //获取、设置指定对象的此属性值
  name.set(p,"Tom");
  System.out.println(name.get(p));
  ```

- getDeclaredMethod():参数1 ：指明获取的==方法==的名称  参数2：指明获取的方法的形参列表

  ```java
  //getDeclaredMethod():参数1 ：指明获取的方法的名称  参数2：指明获取的方法的形参列表
  Method show = clazz.getDeclaredMethod("show", String.class);
  //2.保证当前方法是可访问的
  show.setAccessible(true);
  //3. 调用方法的invoke():参数1：方法的调用者  参数2：给方法形参赋值的实参invoke()的返回值即为对应类中调用的方法的返回值。
  Object returnValue = show.invoke(p,"CHN"); //String nation = p.show("CHN");
  ```

- ==获取指定的构造器==

  ```java
  //getDeclaredConstructor():参数：指明构造器的参数列表
  Constructor constructor = clazz.getDeclaredConstructor(String.class);
  //2.保证此构造器是可访问的
  constructor.setAccessible(true);
  //3.调用此构造器创建运行时类的对象
  Person per = (Person) constructor.newInstance("Tom");
  ```

##### 反射的应用——动态代理

静态代理：代理类和被代理类在编译期间，就确定下来了。

# MySQL核心技术

## 为什么学数据库

1. 实现数据的持久化
2. 使用完整的管理系统统一管理，易于查询

## 数据库的相关概念

#### DB

database是存储数据的仓库，保存了一系列有组织的数据

#### DBMS

Database Management System ，又称为数据库软件（产品），用于管理DB中的数据

#### SQL

Structure Query Language （结构化查询语言）：专门用来与数据库通信的语言。几乎所有的数据库软件都支持SQL

## 数据库存储数据的的特点

1. 先将数据放在表中，再把表放到库中
2. 一个数据库可以有多个表，每个表都有名字，表名具有唯一性
3. 表具有一些特性，定义了数据在表中如何存储，类似于---  “类”
4. 表由列组成，也称为==字段==。所有表都由一个或多个列组成，每一列类似于Java中的 --- “属性”。
5. 表中的数据是按行存储的，每一行类似于Java中的 --- “对象”

## MySQL基础

一、数据库概述
1、为什么要用数据库？
程序中的数据是在内存中，一旦程序关了，数据就没了，没法永久保存。
所以我们需要把数据“持久化”。

我们虽然学过IO流和File类，可以实现数据的持久化，但是用普通的文件保存的话
（1）数据的格式
（2）检索、管理（增加、修改、删除）等操作及其不方便

因此我们要用特殊的文件来存储我们的数据，这个特殊的文件就是数据库。
数据库就是有组织/有结构的方式来存储我们的数据。

结论：
（1）数据“持久化”。
（2）有组织/有结构的方式来存储我们的数据，更方便增、删、改、查...

2、什么是数据库
DB：Database，数据库->数据仓库，存储数据用的，并有结构的存储。
DBMS：Database Management  System  数据库管理系统，
​	mysql,oracle,sql server, access, redis,mango db...
SQL:Structured 	Query Language 结构化查询语言

3、安装DBMS

4、mysql属于==关系型数据库== 
二维（行、列）表格的形式

mysql的DBMS系统中会有很多库DB，
但是一个DB数据库中又会有很多张表格table，
每一个表格中会有很多的列column和行record。

#### MySQL软件

MySQL、Oracle、SqlServer都属于C/S型软件，需要安装客户端和服务端，一般我们在开发时都是安装的服务端

## 1. 启动、登录和登出服务器

注意：我们刚才安装的 mysql 是==服务器端== 的程序。
我们使用时要分为两步：启动 + 登录

#### 检查服务的启动与停止

任务管理器-->服务-->mysql5.5

方式一：计算机，右键 --> 管理 -->  服务和应用程序 --> MySQL --> 启动/停止

方式二 ： 以管理员的方式启动cmd，执行：

```shell
//启动
net start mysql//
//停止
net stop mysql//mysql是安装时自己设置的MySQL软件的名字
```

#### MySQL服务的登录和退出

方式一：通过mysql自带的客户端，只限于root用户

方式二：通过windows自带的客户端

```
//登录：
mysql 【-h主机名 -P端口号 】-u用户名 -p密码
如：
mysql -h localhost -P 3306 -u root -p
mysql -u root -p
//退出：
exit或ctrl+C
```

## 2. 客户端连接服务器端

客户端的种类有很多，常见的：
（1）命令行客户端
（2）Java程序
（3）可视化工具，SQLyog，Navicat，Mysql admin....

## 3. 使用命令行客户端

（1）确定环境变量正确
可以使用mysql命令
（2）mysql命令的格式：
mysql -h localhost -P 3306 -u root -p
Enter password:密码

说明：
（1）-h,-P,-u后面可以有空格也可以没有空格，但是最后-p后面不要加空格
（2）如果你是默认连接本机localhost，那么可以省略-h localhost
（3）如果你是默认用 ==3306== 端口号，那么可以省略-P 3306

## 4. 常见命令

##### 1. 创建、查看数据库

```mysql
CREATE DATABASE name;   //创建数据库name
show databases;   //查看当前所有的数据库
```

##### 2. 打开指定的库  

```mysql
use 库名
```

##### 3. 查看库的所有表

```mysql
show tables; //查看当前库的所有表
show tables from 库名; //查看其它库的所有表
```

##### 4. 创建表

```mysql
create table 表名(

列名 列类型,
列名 列类型，
。。。
);
//如：
create table firstTable(
    id int,
    name varchar(20),
    age int
    );
```

##### 5. 查看表中的数据

```mysql
select * from firstTable;
```

##### 6. 在表中添加记录

```mysql
insert into test.firstTable values(1,'吴猪猪',23);
```

注：如果客户端（现在用的terminal）编码是GBK，可以通过如下的语句，告知服务器当前的客户端是GBK。

```mysql
set names gbk;
```

1. 查看表结构

```mysql
desc 表名;
```

## 5. MySql 的数据类型

##### 1. 整型

```mysql
Java：byte,short,int,long
mysql：
tinyint     byte  1个字节   -128~127, unsigned 0~255
smallint    short 2个字节
mediumint         3个字节
int				 4个字节
bigint	    long  8个字节
```

例如：
id int(8)  等价于 int(11)，

`int(8)` 与`int(11)`后的括号中的字符表示==显示==宽度，整数列的显示宽度与 MySQL 需要用多少个字符来显示该列数值，与该整数需要的==存储空间的大小==都没有关系

int(M)：这个 M 是指==最大显示宽度== ，如果单独使用(M)是没有意义，必须结合 ==zerofill unsigned== 

id int(8) zerofill unsigned： 1表示为：00000001

##### 2. 浮点型

```java
Java：float,double
mysql：float,double

mysql中的float和double可以指定宽度和精度
double(M,D)，例如：double(5,2)  存储范围是-999.99~999.99
	   M是一共有几位，D表示小数点后有几位
double(M,D) unsigned	，例如：double(5,2) unsigned  存储范围：0~999.99
```

##### 3. 定点型

Java：BigDecimal,BigInteger
mysql：DECIMAL和NUMERIC  都是可以表示小数

##### 4. 日期时间类型

```mysql
Java：java.sql.Date,java.sql.Time,java.sql.Timestamp
mysql：date,time,timestamp,datetime,year
date：日期
time：时间
timestamp,datetime：日期加时间
year：只有年份

timestamp,datetime：
	timestamp底层是使用毫秒表示，可以区分时区的（同一个毫秒值，在不同的时区，显示的结果是适用当前时区）
	范围：1970 ... ~ 2038....
    datetime是日期和时分秒表示，不区分时区，什么值就是什么值
    范围：1000....~ 9999....
```

##### 5. 字符串类型

```mysql
Java中分为字符类型char和字符串类型String
Mysql没有字符类型，都是字符串类型
	char：也是字符串类型
	varchar：也是字符串类型，如果是varchar，使用时，必须指定varchar(M)
	text：也是字符串类型
	
	char或char(1)表示存1个字符，如果char(M)存储M个字符
	char和varchar的区别：
	char一个是定长字符串，例如：char(8)，'尚'  用'\u0000'补全8位，char的读写速度快
	varchar一个是变长字符串	,例如：varchar(8)，'尚'  实际占尚这个字和这个字的字节数，varchar读写速度慢，节省空间
	例如是UTF-8   占3个字节 + 1个字节（存3这个数字）
```

##### 6. 其他类型

```mysql
xxxbit
xxxblob：二进制类型 	可以存储二维码，小头像
枚举类型：预定义几个值，从中选一个
集合类型：预定义几个值，从中选多个
```

##### 7. 特殊值：null

- 在Java中，只有引用数据类型才能赋值为null

  > 要判断null值，  if(变量 == null)  或 if(变量 !=null)
  >
  > null值不能用来计算，用来计算是要报错

- 在MySQL中，所有类型都可以赋值为null

  > 要判断null值，  is null  或   is  not  null
  > null值用来计算不会报错，但是结果都是null

## 6. Structure Query Language，结构化查询语言

##### 规范

（1）mysql对于SQL语句==不区分大小写== ，SQL语句关键字尽量大写

（2）值，除了数值型，==字符串==型和==日期时间==类型使用单引号  ' '
（3）==列/字段别名==，尽量使用双引号（""），而且不建议省略 as
（4）所有标点符号使用英文状态下的半角输入方式
（5）必须保证所有( ),单引号，双引号是成对结束的
（6）可以使用（1）#单行注释 （2）-- 空格单行注释 （3）/*  多行注释  */

##### 命名规则

（1）必须只能包含 A–Z, a–z, 0–9, _共63个字符
（2）长度不宜过长
（3）==不能包含空格==
（4）不要重名
​	   	  同一张表 字段不能同名，不同的表 字段可以重名
​		  同一个库，表不能重名，不同的库，表可以重名
​		  同一个DBMS中，库不能同名，不同的DBMS系统中，库可以重名
（5）必须保证你的字段没有和保留字、数据库系统或常用方法冲突		
（6）如果某个字段在<u>不同的表中，表示的意思是一样的，那么数据类型必须相同</u>


## 7. SQL 语言

DDL：数据==定义==语言，定义库、表结构用的
DML：数据==操作==语言，增、删、改、查
DCL：数据==控制==语言，权限、事务等控制语句

### 1. DDL

##### 1.1 操作数据库的语句

> show databases;   查看当前DBMS中的所有数据库
> create database 数据库名;  创建一个数据库
>
> drop database 数据库名;   删除一个数据库
>
> use 数据库名;   使用/指定使用哪个数据库，有了这句后，下面的sql都是默认针对这个数据库的操作。

##### 1.2 操作表格的语句

>1. show : 查看某个库的所有表格:
>
>```mysql
>show tables;  #必须前面有use 数据库名;的语句  否则报no database select的错误
>show tables from 数据库名;
>```
>
>2. create：创建表格
>
>   ```mysql
>   //基本版：
>   create table [数据库名.]表名称(
>   	字段名1  数据类型,
>   	字段名2  数据类型,
>   	字段名2  数据类型,
>   	....
>   );
>   create table [数据库名.]表名称(字段名1  数据类型,字段名2  数据类型,字段名2  数据类型,....);
>   ```
>
>   注意：最后一个字段名的数据类型后面就不用加 "," ，例如：
>
>   ```mysql
>   create table employee(
>   	id int,
>   	name varchar(20),
>   	age int,
>   	salary double,
>   	gender char,
>   	birthday date
>   );
>   ```
>
>3. desc ：查询表结构
>
>   ```mysql
>   desc 表名称;
>   ```
>
>4. alter + add : 修改表结构：增加一列
>
>   ```mysql
>   alter table 表名称 add 字段名  数据类型 [after 字段名/ first];
>   #e.g.
>   alter table employee add tel char(11);
>   alter table employee add tel char(11)  after name;
>   ```
>
>5. alter + drop : 修改表结构：删除一==列==
>
>   ```mysql
>   alter table 表名称 drop 字段名;
>   #e.g.
>   alter table employee drop tel;
>   ```
>
>6. alter + modify : 修改表结构：修改列的类型，位置等
>
>   ```mysql
>   alter table 表名称 modify 字段名  数据类型 【after 字段名/ first】;
>   #e.g.
>   alter table employee modify gender char(2) after age;
>   ```
>
>7. alter + change: 修改表结构：修改列的名称
>
>   ```mysql
>   alter table 表名称 change  旧字段名  新的字段名 数据类型 【after 字段名/ first】;
>   #e.g.
>   alter table employee change gender sex char(2) after age;
>   ```
>
>8. alter + rename to : 修改表名称
>
>   ```mysql
>   alter table 表名称  rename to 新名称;
>   #e.g.
>   alter table employee rename to emp;
>   ```
>
>9. drop table删除整张表，包括数据和表结构
>
>   ```mysql
>   drop table 表名称;
>   ```
>

### 2. DML

##### 2.1 insert into : 添加数据

>1. 为表的所有列赋值
>
>   ```mysql
>   insert into 表名称 values(值列表);
>   #e.g.
>   insert into employee values(1,'吴猪猪',22,10000,'男','1997-10-05');
>   ```
>
>2. 为表的部分列赋值
>
>   ```mysql
>   insert into 表名称(字段列表) values(值列表);
>   #e.g.
>   insert into employee(id,name) values(2,'李四');
>   
>   # 一次性增加多行
>   insert into 表名称 values(值列表1),(值列表2),....;
>   insert into 表名称(字段列表) values(值列表1),(值列表2),....;
>   #e.g. 
>   insert into employee(id,name) values(3,'王五'),(4,'赵六'),(5,'钱七');
>   ```

##### 2.2 update + set : 修改数据

```mysql
- update 表名称  set  字段名1 = 字段值1, 字段名2 = 字段值2  [where 条件];
#e.g.  
update employee set gender = '男';# 所有成员的性别都变成男
update employee set age = 24 where name = '李四';
update employee set salary = salary * 2; #给所有人涨薪
```

##### 2.3 delete / truncate 删除数据

```mysql
delete from 表名称 【where 条件】;
#delete e.g.
delete from employee;
delete from employee where name = '赵六';

#truncate
truncate 表名称;
#比较
truncate比delete效率要高。
truncate是不能回滚。因为它是将整张表drop掉，新建一张。而delete是真的一条一条删除的。
```

##### 2.4 查看数据

> 1. 查看所有的数据
>
>    ```mysql
>    select * from 表名称;
>    ```
>
> 2. 查看部分列
>
>    ```mysql
>    select 字段列表 from 表名称;
>    #e.g.
>    select id,name from employee;
>    ```
>
> 3. 查看部分行(==*表示所有==)
>
>    ```mysql
>    select * from 表名称 [where 条件];
>    select 字段列表 from 表名称 [where 条件];
>    #e.g.
>    select * from employee where name ='张三';
>    #查看张三的薪资
>    select salary from employee where name ='张三';
>    ```

##### 2.5 可以在查询结果时，给字段取别名

```mysql
select 字段名1 as "别名1",字段名2 as "别名2" ... from 表名称 [where 条件];
#e.g.
select id as "编号", name as "姓名", salary as "薪资" from employee;
select id  "编 号", name 姓名, salary  薪资 from employee;
```

###### **复习**

> **DDL（至少能够看得懂，如果会就更好了）**
>
> 1. 数据库相关
>
>    > - show databases;
>    >
>    > - use 数据库名;
>    >
>    > - create database 数据库名;
>    >
>    > - drop database 数据库名;
>
> 2. 表结构相关
>
>    > - show tables; 
>    >
>    > - show tables from 数据库名;
>    > - create table 【数据库名.】表名称(
>    >   字段名1 数据类型1,
>    >   字段名2 数据类型2,
>    >   ...
>    >   );
>    > - ==drop== table 表名称;
>    > - desc 表名称;
>    > - alter table 表名称  add 字段名 数据类型 【first/after 另一个字段】;
>    >   alter table 表名称  modify 字段名 数据类型 【first/after 另一个字段】;
>    >   alter table 表名称  change 旧字段名 新字段名 数据类型 【first/after 另一个字段】;
>    >   alter table 表名称  ==drop== 字段名;
>    >   alter table 旧表名称  rename to 新表名;
>
> **DML（必须会写）**
>
> 1. 添加
>
>    > - insert into 表名称 values(值列表);  #要求值列表的数量、顺序与表结构中字段的数量和顺序一致
>    > - insert into 表名称(字段列表) values(值列表); #要求值列表的数量、顺序与前面的字段列表一致
>    > - insert into 表名称(字段列表) values(值列表),(值列表),(值列表)...;
>    > - insert into 表名称 values(值列表),(值列表),(值列表)...;
>
> 2. 修改
>
>    > - update 表名称 set 字段名1 = 值,字段名2 = 值,...  【where 条件】;
>
> 3. 删除
>
>    > ==delete== from 表名称 【where 条件】;
>    >
>    > ==truncate== 表名称;
>
> 4. 查询
>
>    >- select * from 表名称 【where 条件】;
>    >- select 字段列表  from 表名称 【where 条件】;

##### 2.6 约束

目的：使得数据更准确，更完整。
约束的分类：

> 1. 键约束
>
>   - ==主键约束==
>
>     > 1. 概述
>  >
>  >- 关键字 ：primary key
>  >- 特点：增加主键约束的列（字段）的值必须是==非空== + 唯一的，一个表只有一个主键约束
>  >- 作用：保证表中不会出现两条无法区分的记录
>  >- 要求：每一张表都必须有主键约束
>  >- 分类 : 单列主键约束 、复合主键约束
>  >- 
>  >
>  >2. 使用主键约束
>  >
>  >2.1 创建主键约束(primary key)
>  >
>  >- 建表时指定主键约束
>  >
>  >```mysql
>  >create table 【数据库名.】表名称(
>  >	字段1 数据类型 primary key,
>  >	字段2 数据类型,
>  >	....
>  >);
>  >create table dept(
>  >id int,
>  >name varchar(20),
>  >description varchar(20));
>  >create table 【数据库名.】表名称(
>  >	字段1 数据类型,
>  >	字段2 数据类型,
>  >	....,
>  >	primary key(字段1)
>  >);
>  >```
>  >
>  >- 建表后指定主键约束
>  >
>  >```mysql
>  >create table dept(
>  >	id int,
>  >	name varchar(20),
>  >	description varchar(100)
>  >);
>  >修改表结构：
>  >alter table dept add primary key(id);
>  >```
>  >
>  >2.2  删除主键约束
>  >
>  >```mysql
>  >alter table 表名称 drop primary key;
>  >```
>  >
>  >3. ==复合主键==
>  >
>  >3.1 建表时指定主键约束
>  >
>  >> 1. ```mysql
>  >>   create table 【数据库.】表名称(
>  >>   字段1 数据类型,
>  >>   字段2 数据类型,
>  >>   字段3 数据类型,
>  >>   ...,
>  >>   primary key(字段列表)
>  >>   );
>  >>   ```
>  >> #e.g.
>  >> create table score(
>  >> sid int,		#学号
>  >> cid int,		#课程编号
>  >> score int,		#对应的成绩
>  >> primary key(sid,cid)
>  >> );
>  >> ```
>  >> 
>  >> ```
>  >>
>  >> ```
>  >> 
>  >> ```
>  >>
>  >> ```
>  >> 
>  >> ```
>  >>
>  >> ​    说明：复合主键不能在列后面加，需要单独指定
>  >>
>  >> ```
>  >> 
>  >> ```
>  >>
>  >> ```
>  >> 
>  >> ```
>  >>
>  >> ```
>  >> 
>  >> ```
>  >
>  >3.2 建表后指定主键约束
>  >
>  >>alter table 【数据库.】表名称 add primary key(字段列表);
>  >>
>  >>```mysql
>  >>create table stu(
>  >>	sid int,
>  >>    sname varchar(20)
>  >>);
>  >>create table course(
>  >>	cid int,
>  >>    cname varchar(20)
>  >>);
>  >>create table score(
>  >>    sid int,
>  >>    cid int,
>  >>    score int
>  >>);
>  >>insert into stu values(1,'张三'),values(2,'李四');
>  >>insert into course values(1001,'mysql'),(1002,'java');
>  >>insert into score values(1,1001,89),(1,1002,90),(2,1001,88),(2,1002,92);
>  >># score:
>  >>+------+------+-------+
>  >>| sid  | cid  | score |
>  >>+------+------+-------+
>  >>|    1 | 1001 |    89 |
>  >>|    1 | 1002 |    90 |
>  >>|    2 | 1001 |    88 |
>  >>|    2 | 1002 |    92 |
>  >>+------+------+-------+
>  >>sid和cid都可能不止出现一次，于是出现复合主键，将两者一起设置为主键：
>  >>alter table score add primary key(sid,cid);
>  >>
>  >>#也可以通过唯一标记行，不用符合主键
>  >>create table score(
>  >>	id int,			#没有业务意义，只是唯一标记一行
>  >>	sid int,		#学号
>  >>	cid int,		#课程编号
>  >>	score int,		#对应的成绩
>  >>	primary key(id)
>  >>);
>  >>```
>  >
>  >4. ==唯一键约束== 
>  >
>  >- 概述
>  >
>  >> 1、关键字：unique key
>  >> 2、特点：指定了唯一键的列的值必须唯一，不能重复
>  >> 3、作用：给主键以外的列，限定唯一性
>  >> 4、唯一键分类：单列的唯一，复合唯一
>  >>
>  >> 5、唯一键和主键的区别： 
>  >> （1）主键不能为空，唯一键可以为空
>  >> （2）主键约束，一个表只能有一个，而唯一键可以有很多个
>  >
>  >- 使用唯一键
>  >
>  >（1）在建表时
>  >
>  >```mysql
>  >
>  >create table 【数据库名.】表名称(
>  >	字段1 数据类型  primary key,
>  >字段2 数据类型 【unique key】,
>  >字段3 数据类型 【unique key】,
>  >	...
>  >);
>  >或
>  >create table 【数据库名.】表名称(
>  >	字段1 数据类型  primary key,
>  >	字段2 数据类型 ,
>  >	字段3 数据类型 ,
>  >	...,
>  >	unique key(字段2),  #分别唯一
>  >	unique key(字段3)
>  >);
>  >
>  >create table 【数据库名.】表名称(
>  >	字段1 数据类型  primary key,
>  >	字段2 数据类型 ,
>  >	字段3 数据类型 ,
>  >	...,
>  >	unique key(字段列表)  #复合唯一
>  >);
>  >
>  >create table emp(
>  >	eid int primary key,  #员工编号
>  >	ename varchar(20),   #姓名
>  >	cardid varchar(18)  unique key,		#身份证号
>  >	tel varchar(11) unique key
>  >);
>  >
>  >insert into emp values(1,'张三','123456789123456789','12345678912');
>  >insert into emp values(2,'李四','123456789123456788','12345678912');
>  >
>  >mysql> insert into emp values(2,'李四','123456789123456788','12345678912');
>  >ERROR 1062 (23000): Duplicate entry '12345678912' for key 'tel'
>  >```
>  >
>  >(2) 在建表后
>  >
>  >```mysql
>  >alter table 【数据库名.】表名称 add unique key(字段名);
>  >alter table 【数据库名.】表名称 add unique key(字段列表);  #复合唯一
>  >```
>  >
>  >- 删除唯一键
>  >
>  >```mysql
>  >alter table 【数据库名.】表名称 drop index 索引名;
>  >
>  >#如果不知道索引名，可以通过如下的语句查询：
>  >show index from 表名称;
>  >
>  >alter table emp drop unique key;  #错误
>  >alter table emp drop unique key(cardid);  #错误
>  >alter table emp drop index cardid;#正确
>  >```
>  >
>  >索引：index   
>  >​	作用：为了提高查询效率，而设置索引。我们的键约束（主键、唯一键、外键），都会自动创建索引。
>  >​	因为既然你建立键约束，那么该列的值一定很关键，那么在实际中肯定经常用他们的值来查询。
>  >​	因此，为了提高查询效率，会自动在这些列上增加索引。
>  >
>  >5. ==非空约束和默认值约束== 
>  >
>  >- 指定非空约束
>  >
>  >> - 建表时
>  >>
>  >> ```mysql
>  >> create table emp(
>  >> 	eid int primary key,  #员工编号
>  >>   	ename varchar(20) not null,   #姓名
>  >>   	cardid varchar(18)  unique key not null , #身份证号
>  >>   	tel varchar(11) unique key not null,
>  >>   	gender char not null default '男'
>  >>   );
>  >> 
>  >> insert into emp values(1,'张三','111','10086','女');
>  >> insert into emp values(2,'李四','111','女');  #错误的，原因是值的数量和列的数量不匹配
>  >> insert into emp(eid,ename,cardid,gender) values(2,'李四','111','女');   #错误的  因为tel设置非空，但是又没指定默认值
>  >> insert into emp(eid,ename,cardid,tel) values(2,'李四','222','10010'); 
>  >> insert into emp values(3,'王五','3333','10011',default); 
>  >> ```
>  >> 
>  >> - 建表后
>  >>   
>  >>   ```mysql
>  >>   create table 【数据库名.】表名称(
>  >>   	字段1 数据类型 primary key,
>  >>   	字段2 数据类型 【unique key】【not null】【default 默认值】,
>  >>   	字段2 数据类型 【unique key】【not null】【default 默认值】,
>  >>   	...
>  >>   );
>  >>   
>  >>   create table emp(
>  >>   	eid int primary key,  #员工编号
>  >>   	ename varchar(20) not null,   #姓名
>  >>   	cardid varchar(18)  unique key  ,#身份证号
>  >>   	tel varchar(11) unique key ,
>  >>   	gender char 
>  >>   );
>  >>   
>  >>   alter table emp modify cardid varchar(18) unique key  not null;
>  >>   alter table emp modify tel varchar(11)   not null;
>  >>   alter table emp modify gender char not null default '男';
>  >>   ```
>  >
>  >- - 如何去掉非空和默认值约束
>  >
>  >```mysql
>  >alter table emp modify gender char ;
>  >```
>  >
>  >6. ==自增约束== 
>  >
>  >1. 关键字：auto_increment
>  >
>  >2. 特点
>  >
>  >（1）一个表只能有一个自增列
>  >（2）自增列必须是整型的
>  >（3）自增列必须是==键列==，例如：主键，唯一键
>  >
>  >3. 如何指定自增
>  >
>  >```mysql
>  >create table emp(
>  >	eid int primary key auto_increment,
>  >	ename varchar(20) not null
>  >);
>  >#不管eid处设置多少，只要前面设置了值，就会一直增加下去
>  >insert into emp values(2,'张三'); # eid = 2
>  >insert into emp(ename)values('李四');# eid = 3
>  >insert into emp values(0,'王五');# eid = 4
>  >insert into emp values(null,'赵六');# eid = 5
>  >```
>  >
>  >7. ==外键约束==（了解）
>  >
>  >七、外键约束（了解）
>  >外键约束不是必须的，而且现在很多大的公司，数据量比较大时，不建议在数据库层面设计外键，因为他觉得这样效率低，把这个数据的约束挪到代码层面去判断。
>  >
>  >1. 概述
>  >
>  > - 关键字：foreign key
>  >
>  > - 特点：
>  >
>  >   > 1. 约束的是两张表的关系，需要两张表，或者一张表虚拟成两张表
>  >   > 2. 两张表分为主表（父表）和从表（子表），外键的建立/指定是在从表（子表）上建立
>  >   > 3. 被参考的表称为主表，主表的被参考列必须是主键或唯一键
>  >   > 4. 一个表可以有多个外键
>  >
>  >2. 指定外键
>  >
>  > - 建表时指定外键
>  >
>  >   > 要求：
>  >
>  >>
>  >>1. 建表的顺序：先建主表，再建从表。从表的语法：
>  >>       
>  >>```mysql
>  >>create table 【数据库名.】表名称(
>  >>	字段1 数据类型  primary key,
>  >>	字段2 数据类型 【unique key】【not null】【default 默认值】,
>  >>	字段3 数据类型 【unique key】【not null】【default 默认值】,
>  >>	...,
>  >>	foreign key(从表的外键列) references 主表名(主表被参考的列名)
>  >>);
>  >>```
>  >>
>  >>2. 删表的顺序
>  >>先删从表，再删除主表。
>  >>   
>  >>3. 添加/修改从表数据
>  >>       
>  >>
>  >>添加/修改从表记录时，引用主表的列的值必须是存在的。
>  >>例如：添加/修改员工表时，员工所在部门的值必须引用部门表的部门编号，保证该部门编号是存在的。
>  >>     
>  >>4. 删除/修改主表记录
>  >>       
>  >>   - 默认情况下，如果主表的被参考列的值被引用，那么就不能轻易的被删除和修改。
>  >>     
>  >>
>  >> 例如：2号部门被员工引用了，那么这个2号部门就不能被删除，并且2这个编号值不能被修改。
>  >>     
>  >> ```mysql
>  >> foreign key(从表的外键列) references 主表名(主表被参考的列名) 【on update restrict/no action】 【on delete restrict/no action】
>  >> ```
>  >>
>  >>   - 如果在建立外键时，指定了“级联”策略，那么可以做到级联修改和删除
>  >>     
>  >> ```mysql
>  >> foreign key(从表的外键列) references 主表名(主表被参考的列名) 【on update cascade】 【on delete cascade】
>  >> ```
>  >>
>  >>   - C:如果在建立外键时，指定了“置空”策略，那么可以做到主表的记录被修改或删除时，从表的对应字段变为NULL
>  >>     
>  >> ```mysql
>  >> foreign key(从表的外键列) references 主表名(主表被参考的列名) 【on update set null】 【on delete set null】
>  >> ```
>  >>
>  >>```mysql
>  >>#部门表：主表
>  >>create table dept(
>  >>	did int primary key,		#部门编号
>  >>	dname varchar(20) not null unique key,  #部门名称
>  >>	description varchar(100)				#部门简介
>  >>);
>  >>insert into dept values(1,'财务部','发钱的'),(2,'后勤部','发礼物的');
>  >>
>  >>#职位表：主表
>  >>create table job(
>  >>	jid int primary key,		#职位编号
>  >>	title varchar(20) not null , #职位名称
>  >>	description varchar(100)	#职位简介
>  >>);
>  >>insert into job values(1,'会计','算钱的'),(2,'助理','修电脑的');
>  >>
>  >>#员工表：从表
>  >>create table emp(
>  >>	eid int primary key,			#员工编号
>  >>	ename varchar(20) not null,  #员工姓名
>  >>	deptid int,    #所在的部门编号   deptid可以取名did
>  >>	jobid int,     #职位编号
>  >>	foreign key(deptid) references dept(did),
>  >>	foreign key(jobid) references job(jid) on update set null on delete set null
>  >>);
>  >>
>  >>insert into emp values(1,'张三',1,1),(2,'李四',1,1),(3,'王五',2,2),(4,'赵六',2,2);
>  >>```
>  >>
>  >
>  > - 建表后指定外键
>  >
>  >```mysql
>  >alter table 从表名称 add foreign key(从表的字段) references 主表名(主表被参考的列名);
>  >```
>  >
>  >3. 同一张表，自引用
>  >
>  >```mysql
>  >create table emp(
>  >eid int primary key,
>  >ename varchar(20) not null,
>  >managerid int,
>  >foreign key(managerid) references emp(eid);
>  >);
>  >insert into emp values(1,'张三',1);#张三自己管自己
>  >insert into emp values(2,'李四',1);#张三管李四
>  >insert into emp values(3,'王五',2);#李四管王五
>  >```
>  >
>  >4. 删除外键
>  >
>  >```mysql
>  >alter table 从表名称 drop foreign key 外键约束名;
>  >#查看外键约束名
>  >SELECT * FROM information_schema.table_constraints WHERE table_name = '表名称';
>  >```
>  >
>  >8. 
>
>   - 
>
> 

### 3. DCL

#### 客户端：

- 命令行

  ```mysql
  mysql -h 主机地址 -P 端口号 -u 用户名 -p回车
  Enter Password: 密码
  ```

- MySQL

- SQLyog

- Navicat

- JDBC程序

客户端要连接 MsySQL 服务器才能操作数据库

#### 运算符

##### 1. 算术运算符

- 加：+
- 减：-
- 乘：*
- 除：/  或  div
  ​	div只保留整数部分
- 模：%  或  mod

```mysql
#查询员工的姓名和薪资
SELECT ename,salary FROM t_employee;

#查询员工的姓名和原来的薪资和涨薪1000元后的薪资
SELECT ename,salary,salary + 1000 FROM t_employee;

#查询9/4的结果
SELECT 9/4

#查询9/4的结果
SELECT 9 DIV 4

#查询员工的姓名，和每天的薪资，假设每个月的工作日是22天
SELECT ename AS "姓名", salary / 22 AS "日薪" FROM t_employee

#查询9%4的结果
SELECT 9%4, 9 MOD 4;
```

##### 2. 比较运算符

- 大于：>
- 小于：<
- 大于等于：>=
- 小于等于：<=
- 等于：=====    
     赋值和比较都是用 =
- 不等于：!=  或  ==<>== 
- 安全等于：==<=>==，避免与null比较出错

```mysql
#查询薪资大于20000的员工
SELECT * FROM t_employee WHERE salary > 20000;

#查询薪资等于9000
SELECT * FROM t_employee WHERE salary = 9000;

#查询部门编号不是1的员工
SELECT * FROM t_employee WHERE did != 1;
SELECT * FROM t_employee WHERE did <> 1;

#查询奖金比例是NULL的员工
SELECT * FROM t_employee WHERE commission_pct = NULL;#错误的
SELECT * FROM t_employee WHERE commission_pct <=> NULL;
SELECT * FROM t_employee WHERE commission_pct IS NULL;
```

##### 3. 逻辑运算符

- 与：&& 或 and
- 或：|| 或 or
- 非：!  或 not

```mysql
#查询薪资高于10000 并且低于15000的女员工
SELECT * FROM t_employee
WHERE salary > 10000 && salary <15000 AND gender = '女'

#查询薪资高于20000  或者  籍贯是 浙江
SELECT * FROM t_employee
WHERE salary > 20000 || native_place = '浙江';

#查询非浙江籍的男生
SELECT * FROM t_employee
WHERE NOT native_place = '浙江' AND gender = '男';

#查询奖金比例非空的员工
SELECT * FROM t_employee
WHERE commission_pct IS NOT NULL;
```

##### 4. 区间范围和集合运算符

- 区间范围

  > between xx and yy：[xx,yy]
  > not between xx and yy：  小于xx 或 大于yy

- 集合范围

  > in (值列表)
  > not in(值列表)

```mysql
#查询薪资大于等于10000 并且小于等于15000的员工
SELECT * FROM t_employee
WHERE salary BETWEEN 10000 AND 15000;

#查询籍贯是 “浙江”、“北京”、“上海”、“黑龙江”的员工
SELECT * FROM t_employee
WHERE native_place IN ('浙江','上海','北京','黑龙江');

#查询籍贯不是 “浙江”、“北京”、“上海”、“黑龙江”的员工
SELECT * FROM t_employee
WHERE native_place NOT IN ('浙江','上海','北京','黑龙江');
```

##### 5. 模糊查询

- like 'xx'

  > xx可以用占位符：
  >
  > **_**  代表确定的一个字符

-  %：代表是任意个数的字符，0~n个

```mysql
#查询名字中，第二个字是“冰”
SELECT * FROM t_employee
WHERE ename LIKE '_冰%';
```

#### 联合查询

<img src="pic/联合查询.png" width="70%">



关联查询包括：

- 1. 内连接：inner join

  2. 外连接
     （1）左外连接：left join
     （2）右外连接：right join
     （3）全外连接：full join  mysql不支持

  3. 关联查询分类：

     > 关联查询必须有两张或两张以上，以下用两张来示例：
     >
     > 1. A ∩ B  ： 内连接
     >
     > 2. A  ： 左连接
     >
     > 3. A - A ∩ B：左连接
     >
     > 4. B ： 右连接
     >
     > 5. B - A ∩ B ： 右连接
     >
     > 6. A ∪ B
     >
     > 7. A ∪ B - A ∩ B
     >
     >    ​	6、7 本应该用全外连接，现在用 union（序号对应上述连接的序号）
     >    ​	6 = 2  union  4
     >    ​	7 = 3  union 5 

##### 1. 内连接

- 形式一

  ```mysql
  select 字段列表
  from A表 inner join B表 
  on 关联条件 
  【where 其他筛选条件】
  ```

  说明：
     如果不写关联条件，会出现一种现象：==笛卡尔积==
     关联条件的个数 = n - 1，n是几张表关联
     on 只能和 join 一起用


- 形式二

  ```mysql
  select 字段列表
  from A表 , B表
  where 关联条件 【and 其他筛选条件】
  ```

  ```mysql
  #查询所有的员工的姓名和他所在部门的编号和部门的名称，不包括那些没有安排部门的员工
  SELECT ename,did,dname FROM t_employee INNER JOIN t_department  #错误
  #错误：Column 'did' in field list is ambiguous，因为did没有说明是哪个表的
  #方式一
  SELECT ename,t_employee.did,dname 
  FROM t_employee INNER JOIN t_department
  ON t_employee.did = t_department.did
  #方式二
  FROM t_employee , t_department
  WHERE t_employee.did = t_department.did 
  
  #查询所有的==女==员工的姓名和他所在部门的编号和部门的名称，不包括那些没有安排部门的员工
  #方式一
  SELECT ename,t_employee.did,dname 
  FROM t_employee INNER JOIN t_department
  ON t_employee.did = t_department.did
  WHERE gender = '女';
  #方式二
  SELECT ename,t_employee.did,dname 
  FROM t_employee , t_department
  WHERE t_employee.did = t_department.did AND gender = '女'
  
  #查询员工编号，员工的姓名，部门编号，部门名称，职位编号，职位名称
  #需要t_employee,t_department, t_job
  SELECT t_employee.eid, t_employee.`ename`, t_department.did,t_department.`dname`, t_job.`job_id`,t_job.`job_name`
  FROM t_employee INNER JOIN t_department INNER JOIN t_job
  ON t_employee.did = t_department.did AND t_employee.`job_id` = t_job.`job_id`
  
  SELECT t_employee.eid, t_employee.`ename`, t_department.did,t_department.`dname`, t_job.`job_id`,t_job.`job_name`
  FROM t_employee , t_department , t_job
  WHERE t_employee.did = t_department.did AND t_employee.`job_id` = t_job.`job_id`
  ```

##### 2. 左连接

第一种结果：A

```mysql
select 字段列表
from A表 left join B表
on 关联条件
```

第二种结果：A - A∩B

```mysql
select 字段列表
from A表 left join B表
on 关联条件
where 从表的关联字段 is null
```

```mysql
#查询所有员工和他的部门编号，部门名称，包括那些没有部门的员工
SELECT * 
FROM t_employee LEFT JOIN t_department
ON t_employee.did = t_department.did

#查询所有没有部门的员工
##不用关联查询也可以实现
SELECT * FROM t_employee WHERE did IS NULL

##用关联查询
SELECT * 
FROM t_employee LEFT JOIN t_department
ON t_employee.did = t_department.did
WHERE t_employee.did IS NULL
```

##### 3. 右连接

1. 左连接和右连接的区别：

- left换成right
- 左边的表为主还是以右边的表为主

2. 右连接第一种结果：B

   ```mysql
   select 字段列表
   from A表 right join B表
   on 关联条件
   ```

3. 右连接第二种结果：B - A∩B

   ```mysql
   select 字段列表
   from A表 right join B表
   on 关联条件
   where 从表的关联字段 is null
   ```

##### 4. 联合查询

使用union实现全连接的效果

- A ∪ B

  ```mysql
  select 字段列表
  from A表 left join B表
  on 关联条件
  
  union 
  
  select 字段列表
  from A表 right join B表
  on 关联条件
  ```

- A ∪ B - A ∩ B （相当于 A - A∩B  union B - A∩B）

  ```mysql
  select 字段列表
  from A表 left join B表
  on 关联条件
  where 从表的关联字段 is null
  
  union
  
  select 字段列表
  from A表 right join B表
  on 关联条件
  where 从表的关联字段 is null
  ```


```mysql
#查询所有员工和部门信息，包括那些没有部门的员工和没有员工的部门
SELECT *
FROM t_employee LEFT JOIN t_department
ON t_employee.did = t_department.did

UNION

SELECT *
FROM t_employee RIGHT JOIN t_department
ON t_employee.did = t_department.did

#查询那些没有部门的员工和没有员工的部门
/*
where xxx  is null
xxx 看从表

员工表和部门表来说，员工表是从表。
因为主表的字段，例如did是不可能为null
*/
SELECT *
FROM t_employee LEFT JOIN t_department
ON t_employee.did = t_department.did
WHERE t_employee.did IS NULL

UNION 

SELECT *
FROM t_employee RIGHT JOIN t_department
ON t_employee.did = t_department.did
WHERE t_employee.did IS NULL
```

##### 5. 特例：自连接

联合查询需要两张表，现在自连接，就一张表当两张表用。通过给表取别名的方式，把一张表变成“两张表”
表的别名不要加 " "

```mysql
#查询员工的编号，员工的姓名，领导的编号，领导的姓名
#员工的信息和领导的信息都在t_employee表

SELECT emp.eid,emp.ename,emp.`mid`,mgr.ename
FROM t_employee AS emp INNER JOIN t_employee AS mgr  #emp代表员工表，mgr代表领导表
ON emp.`mid` = mgr.`eid`  #员工的领导编号 = 领导的员工编号
```

#### select 的5个子句

之前：

```mysql
select * from 表名称 【where 条件】;
select 字段列表 from 表名称 【where 条件】;
```

现在select语句的5个子句：

- > - where
  >
  >   where 条件   用于从表中筛选出符合条件的记录（行）
  >
  > - group by
  >
  > - having
  >
  > - order by
  >
  > - limit



这5个子句可以同时出现，也可以只出现其中的一部分，其中如果有having前面得有group by，但是有group by不一定有having
如果5个子句有多个==同时出现的，那么必须按照（1）-（5）的顺序==
例如：要分组统计之前，需要把满足条件的行先筛选出来，或者说把不满足条件的行排除掉才能统计

##### 1. where

```mysql
#查询所有的女员工
SELECT * FROM t_employee WHERE gender = '女';

#查询所有女员工的姓名和薪资
SELECT ename,salary FROM t_employee WHERE gender = '女';
```

**分组函数**

| sum  | count | avg  | max  | min  |
| ---- | ----- | ---- | ---- | ---- |
|      |       |      |      |      |

```mysql
#查询全公司本月要发多少钱，暂时不考虑奖金和扣除的钱
#即查询全公司所有员工的工资总数
SELECT SUM(salary) AS "工资总数" FROM t_employee;

#查询全公司的员工总数
SELECT COUNT(eid) AS "总人数" FROM t_employee;  #如果count(字段名)那么会排除该字段是null值的行
SELECT COUNT(1) AS "总人数" FROM t_employee;    #如果count(常量值)或count(*)那么统计的是行数
SELECT COUNT(*) AS "总人数" FROM t_employee;

#查询全公司的平均工资
SELECT AVG(salary) AS "全公司的平均工资" FROM t_employee;

#查询全公司的最高工资
SELECT MAX(salary) AS "全公司的最高工资" FROM t_employee;

#查询全公司的最低工资
SELECT MIN(salary) AS "全公司的最低工资" FROM t_employee;

#查询全公司的女员工的平均工资和最高工资、总工资
SELECT AVG(salary),MAX(salary),SUM(salary) FROM t_employee WHERE gender = '女';

#查询did=5部门的女员工的平均工资和最高工资、总工资
SELECT AVG(salary),MAX(salary),SUM(salary) FROM t_employee WHERE gender = '女' AND did = 5;
```

##### 2. group by : 分组统计

```mysql
#查询每个部门的平均工资
SELECT did,AVG(salary) FROM t_employee GROUP BY did;

#查询每个部门的平均工资，排除没有部门的员工
SELECT did,AVG(salary) FROM t_employee WHERE did IS NOT NULL GROUP BY did ;

#查询每个部门编号，部门名称，和平均工资，排除没有部门的员工
#需要联合查询
#用SELECT did,AVG(salary) FROM t_employee WHERE did IS NOT NULL GROUP BY did ;结果和部门表联合查询

#查询每个部门的女员工的最高工资
SELECT did,MAX(salary) FROM t_employee WHERE gender = '女' GROUP BY did;
SELECT did,MAX(salary) FROM t_employee WHERE gender = '女' AND did IS NOT NULL GROUP BY did;

#查询男、女员工的平均工资
SELECT gender,AVG(salary) FROM t_employee GROUP BY gender;

#查询每个部门的男、女员工的平均工资分别是多少
#先按部门再按男女
SELECT did, gender, AVG(salary) FROM t_employee GROUP BY did,gender;
SELECT did, gender, AVG(salary) FROM t_employee WHERE did IS NOT NULL GROUP BY did,gender;

#查询每个部门的工资总数
SELECT did,SUM(salary) FROM t_employee GROUP BY did;

#查询每个部门的男、女员工的人数
SELECT did, gender, COUNT(*) FROM t_employee WHERE did IS NOT NULL GROUP BY did,gender;
```

##### 3. having：写条件

where和having的区别：

- where后面是不允许使用分组函数，having后面可以加分组函数
- where是用于“原”表中的记录的筛选，而having是用于“统计结果”的筛选

```mysql
#查询每个部门的平均工资，只显示平均工资在12000以上的
SELECT did,AVG(salary) FROM t_employee  GROUP BY did HAVING AVG(salary) > 12000

#查询每个部门的最高工资，要求显示最高工资低于12000
SELECT did,MAX(salary) FROM t_employee GROUP BY did HAVING MAX(salary) < 12000
SELECT did,MAX(salary) AS "m" FROM t_employee GROUP BY did HAVING m < 12000
```

##### 4. order by：排序

```mysql
order by 字段名/统计结果 【DESC/ASC】, 字段名/统计结果 【DESC/ASC】 ...
DESC ：降序
ASC：升序
```

```mysql
#查询员工的姓名和薪资，按照薪资的从高到低排序
SELECT ename,salary FROM t_employee ORDER BY salary DESC;

#查询员工的编号，姓名和薪资，按照薪资的从高到低排序，如果薪资相同，再按照编号升序排列
SELECT eid,ename,salary FROM t_employee ORDER BY salary DESC,eid ASC;

#查询每个部门的平均工资，按照平均工资的升序排序
SELECT did,AVG(salary) FROM t_employee GROUP BY did ORDER BY AVG(salary) ASC;

#查询每个部门的女员工的平均工资，按照平均工资的升序排序，并且只显示平均工资高于12000的
SELECT did,AVG(salary) 
FROM t_employee 
WHERE gender = '女' 
GROUP BY did 
HAVING AVG(salary) > 12000
ORDER BY AVG(salary) ASC;
```

##### 5. limit：分页显示

```mysql
limit m,n
m = (page - 1)*每页的记录数
n = 每页的记录数
```

```mysql
#查询员工信息，每页显示10条，显示第一页
SELECT * FROM t_employee LIMIT 0,10

#查询员工信息，每页显示10条，显示第二页
SELECT * FROM t_employee LIMIT 10,10

#查询员工信息，每页显示5条，显示第三页
SELECT * FROM t_employee LIMIT 10,5

#查询每个部门的女员工的平均工资，按照平均工资的升序排序，并且只显示平均工资高于12000的，
#每页显示1条，显示第二页
SELECT did,AVG(salary) 
FROM t_employee 
WHERE gender = '女' 
GROUP BY did 
HAVING AVG(salary) > 12000
ORDER BY AVG(salary) ASC
LIMIT 1,1;
```

#### 子查询

场景：当进行一个查询时，需要的条件或数据要用另外一个 select 语句的结果，这个时候，就要用到子查询。

定义：先于当前查询执行的，并且是嵌套在当前查询中的查询叫做子查询。

分类：

1. where 型

   定义：子查询嵌套在where + 条件 里面

   条件的运算符分为两类：

   > - =，>，>=，<，<=，!=  后面接子查询的结果必须是 ==“单值”== 
   > - in，= any，>all，>= ，<all.....  后面接子查询的结果可以是 ==“多值”== 

2. from 型
   定义：子查询嵌套在from后面

3. exists型

   子查询嵌套在where exists后面，把where前面的查询的每一行的记录代入exists后面的子查询中，看是否是否有记录，如果有，就保留这个行，否则就去掉。


```mysql
################  where型  #################

#查询全公司最高工资的员工的信息
#(1)查询最高工资
SELECT MAX(salary) FROM t_employee;

#(2)查询最高工资的员工的信息
SELECT * FROM t_employee WHERE salary = 130990

#(3)合起来
SELECT * FROM t_employee WHERE salary = (SELECT MAX(salary) FROM t_employee)

#查询和孙红雷，刘烨，范冰冰三个人中任意一个工资一样的员工
#查询孙红雷，刘烨，范冰冰三个人工资
SELECT salary FROM t_employee WHERE ename IN ('孙红雷','刘烨','范冰冰');

#查询和孙红雷，刘烨，范冰冰三个人中任意一个工资一样的员工
SELECT * FROM t_employee WHERE salary IN (SELECT salary FROM t_employee WHERE ename IN ('孙红雷','刘烨','范冰冰'))
SELECT * FROM t_employee WHERE salary = ANY (SELECT salary FROM t_employee WHERE ename IN ('孙红雷','刘烨','范冰冰'))

#查询比李冰冰工资高的女员工
SELECT * FROM t_employee WHERE gender = '女' AND salary > (SELECT salary FROM t_employee WHERE ename = '李冰冰');

#查询全公司最高工资的员工的信息
SELECT * FROM t_employee WHERE salary >= ALL(SELECT salary FROM t_employee)

###################  from型  ###################

#查询每个部门编号，部门名称，和平均工资，排除没有部门的员工，包括那些没有员工的部门
#第一步，查询每个部门的平均工资，排除没有部门的员工
SELECT did,AVG(salary) FROM t_employee  WHERE did IS NOT NULL GROUP BY did;

#第二步：用刚才的结果和t_department联合查询
SELECT t_department.*, temp.pingjun
FROM t_department LEFT JOIN (SELECT did,AVG(salary) AS pingjun FROM t_employee  WHERE did IS NOT NULL GROUP BY did) AS temp
ON t_department.did = temp.did

#################  exists型  ######################

#查询部门信息，该部门必须有员工
SELECT * FROM t_department
WHERE EXISTS (SELECT * FROM t_employee WHERE t_employee.did = t_department.did)

#把SELECT * FROM t_department的每一行记录，根据t_employee.did = t_department.did，代入到(SELECT * FROM t_employee)中查，如果可以查到结果，说明该行要留下，否则就排除掉

#查询部门信息，该部门必须有员工
#使用内连接查询，也可以实现
SELECT  DISTINCT t_department.* 
FROM t_department INNER JOIN t_employee
ON t_employee.did = t_department.did

SELECT  t_department.* 
FROM t_department INNER JOIN t_employee
ON t_employee.did = t_department.did
GROUP BY did
```

#### 函数

##### 1. 单行函数：数学函数

单行函数和分组函数：

- 单行函数：只对某一行的记录做运算

- 分组函数：多行一起统计/合计运算

  > sum,count,avg,max,min都是针对多行求一个结果



数学函数：

- round(x,y)：小数点后取 y 位,并且四舍五入
- truncate(x,y)：直接截掉，保留 x 的小数点后取 y 位

```mysql
#查询员工的姓名，薪资，薪资保留小数点后一位
SELECT ename,salary,ROUND(salary,1) FROM t_employee;

#查询员工的姓名，薪资，薪资保留小数点后一位
SELECT ename,salary,TRUNCATE(salary,1) FROM t_employee;

#select ceil(2.2),floor(2,2);
SELECT CEIL(2.2),FLOOR(2.2);

#求每个部门的平均工资
SELECT did, ROUND(AVG(salary),2) FROM t_employee GROUP BY did;
```

##### 2. 字符串函数

```mysql
#查询每个员工的姓，不考虑复姓
SELECT ename AS "姓名", LEFT(ename,1) AS "姓" FROM t_employee;

/*
java：下标从 0 开始，
	str.substring(index)
	str.substring(start,end)

mysql：下标从 1 开始
	substring(str,index)
	substring(str,start,len)
*/

SELECT ename AS "姓名", SUBSTRING(ename,1,1) AS "姓" FROM t_employee;

#查询员工的姓名的长度
/*
java中：
str.length()
mysql中：
length(str)：求字符串的长度，字节数
char_length(str)
*/
SELECT ename, LENGTH(ename) FROM t_employee;
SELECT ename, CHAR_LENGTH(ename) FROM t_employee;

#查询所有名字是3个字的员工
SELECT * FROM t_employee WHERE CHAR_LENGTH(ename) = 3;

/*
java中字符串拼接：
（1）+
（2）str.concat(xx)
mysql中字符串的拼接：
只能用concat()

在mysql中的+，都是求和，如果不是数字，会尽力而为求和，结果不一定对
*/
#查询员工的姓名和手机号码，结果要显示为：孙红雷:13789098765
SELECT CONCAT(ename,':',tel) FROM t_employee;

/*
在java中trim()表示去掉前后空白格
在mysql中，trim系列的函数
*/
SELECT CONCAT('[',TRIM('     hello world    '),']')
SELECT CONCAT('[',LTRIM('     hello world    '),']')
SELECT CONCAT('[',RTRIM('     hello world    '),']')


SELECT CONCAT('[',TRIM(BOTH '&' FROM '&&&&&hello world&&&&'),']')
SELECT CONCAT('[',TRIM(LEADING '&' FROM '&&&&&hello world&&&&'),']')
SELECT CONCAT('[',TRIM(TRAILING '&' FROM '&&&&&hello world&&&&'),']')
```

##### 3. 日期时间函数

```mysql
#获取当前的系统时间
SELECT NOW(),SYSDATE()
SELECT CURRENT_DATE(),CURRENT_TIME()

#查询当前的年份
SELECT YEAR(CURRENT_DATE())

#查询满足40岁的员工
SELECT * FROM t_employee WHERE YEAR(NOW()) - YEAR(birthday) > 40

#查询入职已经满5年的员工
SELECT * FROM t_employee 
WHERE YEAR(NOW()) - YEAR(hiredate) > 5;

SELECT * FROM t_employee WHERE (DATEDIFF(CURRENT_DATE(),hiredate) DIV 365) >=5;


#计算当前日期，再过130天是什么日期
SELECT DATE_ADD(CURRENT_DATE(),INTERVAL  130 DAY)

#计算当前日期，45天前是什么日期
SELECT DATE_ADD(CURRENT_DATE(),INTERVAL  -45 DAY)

/*
除了在JAVA中可以把字符串转日期时间，或者把日期时间转字符串，
在mysql中也可以
*/
SELECT DATE_FORMAT(NOW(),'%y年%c月%e日');

SELECT STR_TO_DATE('19年1月18日','%y年%c月%e日')
```

##### 4. 控制流程语句

在Java中有if..else,switch...case等流程控制语句结构
mysql中有对应的函数

> 1. ifnull(x,value)：如果x是null，就用value计算，否则还是用x计算
> 2. CASE 
>    WHEN 条件1 THEN result1
>    WHEN 条件2 THEN result2
>    ....
>    [ELSE resultn]
>    END

```mysql
#查询员工的姓名，薪资，奖金比例，实发工资
#实发工资 = 薪资 + 薪资 * 奖金比例
SELECT ename,salary,commission_pct, salary + salary * IFNULL(commission_pct,0)  AS "实发工资" FROM t_employee;

/*查询员工的信息，
如果薪资高于20000，显示该员工是“高富帅”，
如果薪资在15000-20000之间，显示“潜力股”
如果薪资在10000-15000之间，显示“有为青年”
如果薪资在10000以下，显示“屌丝"

相当于if...else if...
*/
SELECT ename, salary, 
CASE
WHEN salary>=20000 THEN "高富帅"
WHEN salary>=15000 THEN "潜力股"
WHEN salary>=10000 THEN "有为青年"
ELSE "屌丝"
END AS "标签" #取别名
FROM t_employee;

#查询订单表，显示订单编号，和订单状态，如果订单状态是0，显示新订单，是1，显示已付款...
/*
相当于switch...case
*/
SELECT oid ,price,
CASE state
WHEN 0 THEN "新建订单"
WHEN 1 THEN "已付款"
WHEN 2 THEN "已发货"
WHEN 3 THEN "已收货"
END
FROM t_order
```

##### 5. 加密函数

1. password(x)

2. md5(x)

   ```mysql
   insert into album (id,name, limit, userid) values (3,'accp',MD5('123456'));
   INSERT INTO user VALUES(3,'kmd33',MD5('1234567'));
   ```

   password在新版本中不能用了，建议用MD5

```mysql
INSERT INTO t_user VALUES(2,'lin',PASSWORD('123456'));
INSERT INTO t_user VALUES(3,'yan',MD5('123456'));

SELECT * FROM t_user WHERE username='lin' AND `password` = PASSWORD('123456');#需要解密
```

#### 事务

定义：表示一组操作（sql），要么同时成功，要么同时失败，那么这种操作就构成了一个事务。
例如：

> 张三  给  李四  转账  500元
>
> 1. 把张三的余额减少500
>
>    ​	...
>
> 2. 把李四的余额增加500



不允许出现：张三的钱减少了500，而李四的钱没有加。需要在（1）之前开启事务，如果同时成功，那么就提交这个事务，否则就回滚（还原到（1））之前的状态。



##### 1. 开启事务

```mysql
start transaction;
```

##### 2. 提交/回滚事务

```mysql
commit;
rollback;
```

mysql默认情况下是自动提交事务模式，即执行一句，自动提交一句，一旦提交就不能回滚。如果想要开始手动提交模式，那么可以通过以下语句完成： `set autocommit = false;`

**手动提交模式**

如果开始了手动提交模式，那么一组 sql 语句，直到 commit 或 rollback 才算是结束，从这个 commit/rollback 到下一个 commit 或 rollback 之间算是一个==事务==。<u> 每一组操作都要手动提交或回滚</u> 。

**自动提交模式** 

总的来说使用自动提交模式，单独的一组操作想要开始手动提交模式的话，可以使用

```mysql
start transaction;  #只能用于命令行，不能用于JDBC的Java代码
#...
commit; #或 rollback;
```





```mysql
#开启手动提交模式，作用范围是一次连接（从登录到退出）
SET autocommit = FALSE;

DELETE FROM t_department WHERE did > 5;

INSERT INTO t_department VALUES(NULL,'yy','yyyy');

ROLLBACK;
#COMMIT;

SET autocommit = TRUE;

DELETE FROM t_department WHERE did > 5;

START TRANSACTION;
INSERT INTO t_department VALUES(NULL,'yy','yyyy');
UPDATE t_department SET dname = '后勤服务部' WHERE did = 5;
COMMIT;
```

[面试题](#1.  事务的特点、特性？)

##### 3. 事务的隔离

事务的隔离级别：

1、为什么要隔离？
保证事务的独立的。
但是很多时候，事务之间有互相影响的。两个事务对同一个表的同一个记录的修改，这就互相影响了。

在Java中就是线程安全问题。在mysql中这种问题也是线程安全问题。那么它表现出来的问题现象：

1. 脏读
   一个事务读取了另一个事务还未提交的数据

2. 不可重复读

   一个事务读取了另一个事务“修改”已提交的数据，导致一个事务期间对同一个数据的前后两次读取，结果不一致。

3. 幻读
   ​     一个事务读取了另一个事务新增加并已经提交的数据，导致一个事务期间记录数不一样。
   ​     一个事务读取了另一个事务删除并已经提交的数据，导致一个事务期间记录数不一样。

mysql的默认隔离级别是：（3）
（1）READ-UNCOMMITTED：读取未提交的数据
（2）READ-COMMITTED：读取已提交的数据
（3）REPEATABLE-READ：可重复读取
（4）SERIALIZABLE：序列化
serializable

查看当前连接的隔离级别：select @@tx_isolation;
修改当前连接的隔离级别：set tx_isolation = 'READ-UNCOMMITTED';

如果当前连接的隔离级别是READ-UNCOMMITTED，你会读取到别人未提交的数据，这个现象称为==脏读== 。
如果避免“脏读”，就是提高隔离级别，提高为READ-COMMITTED或它以上。

如果当前连接的隔离级别是READ-UNCOMMITTED和READ-COMMITTED，都会出现不可重复的的现象，
如果要避免“不可重复读”，还是提高隔离级别，提高为REPEATABLE-READ或它以上。

（3）REPEATABLE-READ和（4）SERIALIZABLE都能避免脏读、不可重复读、幻读，那么有什么区别呢？
REPEATABLE-READ：行
SERIALIZABLE：表

#### 用户与权限

mysql的权限验证分两个阶段

1. 能否连接

   - mysql 的用户的 ==认证==：==主机地址 + 用户名 + 密码==
   - 如果主机地址写 %，就表示任意 IP 都可以访问
   - 如果主机地址写 localhost，那么说明只能本机并且用localhost/127.0.0.1 才能访问

2. 验证权限

   - A：全局权限，针对所有库，所有表，所有字段的权限

     如果某个操作有全局权限，那么就不判断对象级别权限了

   - B：对象级别权限
        库 --> 表 --> 字段   
        每一种操作单独设置权限。

# JDBC

## 1. 什么是JDBC

- Java Database Connectivity：Java数据库连接

- JDBC是一组API，一个独立于特定 DBMS 的、通用的SQL 数据库存取和操作的公共接口。
- SUM公司为了使得 Java 代码可以==跨数据库==，设计了一组公共的接口（标准），规定了所有操作数据库的代码应该用那些类型和方法。JDBC为访问<u>不同的数据库提供了统一的途径</u>
- 这些**操作数据库底层的具体代码**由数据库厂商来实现，这些实现类称为==数据库驱动（Driver)== 。要连接哪个数据库就要拿到该数据库的驱动。
-  Java 中通过 ==接口 + 驱动 + 标准的 SQL 语句==，就可以实现 Java 代码与各种数据库的连接操作
- JDBC API 是 SUM 公司提供的，而这些==接口的实现类（Driver）==是由数据库厂商提供的

```mermaid
graph TD
	Java-application --调用--> JDBC
	JDBC --实现--> id1((Mysql))
	JDBC --实现--> id2((Oracle))
	JDBC --实现--> id3((SQLServer))
	JDBC --实现--> id4((DB2))
```

## 2. 获取数据库连接

##### 1. 导入驱动的 jar 包

- 在 Project Structure 中将 jar 包导入 Library。

- 如果是 Java 工程，需要在工程下创建 lib 文件夹，然后把 jar 包复制到该目录下，且将其标记为 Library
- 如果的 web 工程，直接第一步就够了

##### 2. 注册驱动，加载驱动类到内存中，即在内存中有驱动类的Class对象

```java
//在main方法中写：
String driverClass = "com.mysql.cj.jdbc.Driver";
Class.forName(driverClass);
```

##### 3. 获取连接，即登录，要用URL : 统一资源定位符

```tex
URL: http://localhost:8080/day31/index.html
	 协议//主机地址:端口号/文件路径

MySQL：
	jdbc:mysql://localhost:3306/test
	主协议:子协议://主机地址:端口号/数据库名
```

用到的API：

- java.sql.Connection;
- java.sql.DriverManager;

```java
//获取连接
String url = "jdbc:mysql://localhost:3306/test?serverTimezone=UTC";
String uer = "root";
String password = "12345c";//注意 mysql 登陆密码不要写错
Connection connection = DriverManager.getConnection(url,uer,password);
```

##### 4. 传输/执行SQL

```java
//执行sql

//编写sql语句
String sql = "insert into user values(4,'测试名','测试密码')";

//创建Statement对象
Statement st = connection.createStatement();

//处理执行结果: 获取更新的行数
int len = st.executeUpdate(sql);//insert,update,delete都会更新数据库，select是查询Query
System.out.println(len > 0 ? "添加成功" : "添加失败");

```

##### 6. 释放资源

```java
//关闭资源
st.close();
connection.close();
```

##### 遇到的问题总结

- 报错找不到驱动类

  > 解决：新版本的 jdbc 驱动由原来的 `com.mysql.jdbc.Driver` 变成了 `com.mysql.cj.jdbc.Driver` 。如果建立的是 Java 工程，需要在工程下建一个 lib 文件夹，把驱动的 jar 包导入 并标记为 Library

- 服务器拒绝访问

  > 登录密码写错了

- 时间不匹配

  >  在 url 后加上：`?serverTimezone=UTC`
  >
  > ```java
  > String url = "jdbc:mysql://localhost:3306/test?serverTimezone=UTC";
  > ```

## 3. JDBC 操作与连接池

### 1. Statement 的三个问题

#### 1. 1sql 拼接

> Statement的第一个问题：需要 sql 的拼接，很麻烦。
>
> ```java
> String sql = "INSERT INTO employee(ename,age,salary,gender) VALUES('" + ename + "','"+age+"','"+salary+"','"+ gender +"')";
> ```
>
> 这里 employee 的字段没有按顺序，所以叫拼接



##### PreparedStatement 解决拼接问题

```java
//编写 sql
String sql = "INSERT INTO employee(ename,age,salary,gender) VALUES(?,?,?,?)";

//创建 PreparedStatement 对象
//Statement st = connection.createStatement();
PreparedStatement pst = connection.prepareStatement(sql);//先传入 sql，对带？的sql进行预编译

//把问号的具体值传入
pst.setObject(1,ename);
pst.setObject(2,age);
pst.setObject(3,salary);
pst.setObject(4,gender);

//执行更新sql
//int len = st.executeUpdate(sql);
int len = pst.executeUpdate();//括号内不需要再赋值sql了
```

#### 1.2 sql 注入

Statement的第二个问题：sql 注入，==盗窃信息== 

```java
输入 : cxy
输出 ：可得到cxy的信息

输入 ：胡歌' or '1'='1
输出 : 表内所有
```

```java
String sql = "select * from employee where ename = '"+ename+"'";
// 输入：cxy' or '1'='1，带入上式：select * from employee where ename = 'cxy' or '1'='1'。or 后面的条件恒成立，故输出所有
```

PreparedStatement 解决注入问题 类似解决拼接问题。

#### 1.3 处理blob 等类型

Statement的第三个问题：sql 拼接不支持 blob  等二进制类型类型

PreparedStatement 解决blob 等类型

```java
//读取图片
FileInputStream fis = new FileInputStream("E:\\Pictures\\ww1.jpg");
//...
//编写 sql
String sql = "UPDATE employee SET PHOTO = ? WHERE ename = '刘亦菲';";
pst.setObject(1,fis);
//...
```

在表格中新建一列命名为 photo，格式选择Mediumblob（最大传输16M），再在 mysql 安装目录下的my.ini文件中写下：

```ini
max_allowed_packet=16M
```

### 2. JDBC 获取数据库自动生成的主键

- Statement 是 PreparedStatement 的父接口

* 在Statement 接口中有个常量值：RETURN_GENERATED_KEYS

```java
String sql = "INSERT INTO dept VALUES(NULL,?,?)";

//Statement.RETURN_GENERATED_KEYS表示执行完 sql 后，返回自增长的键值
PreparedStatement pst = connection.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS);

ResultSet generatedKeys = pst.getGeneratedKeys();//获取自增长的键值，被包装在一个ResultSet 的结果集中
if(generatedKeys.next()){//自增长的键值只有一个单值
    System.out.println("部门编号：" + generatedKeys.getObject(1));
}
```

### 3. 批处理

从excel等文件中获把原始数据迁移到当前数据库中时，用批处理可减少工作量

- addPath() ：把sql 语句先添加到批处理命令中缓存起来

- executeBatch()：执行批处理语句

```java
	String sql = "INSERT INTO dept VALUES(NULL,?,?)";
	PreparedStatement pst = connection.prepareStatement(sql);

     for (int i = 1; i <= 1000; i++) {
            pst.setObject(1,"测试部门" + i);
            pst.setObject(2,"测试简介" + i);
            pst.addBatch();//添加到批处理。先缓存，缓存满之后会自动执行一批
      }

      //返回1000个结果
      int[] results = pst.executeBatch();
```

* 注意：
* 在 url 后面加一个数据：?rewriteBatchedStatements=true
* 添加数据时用 VALUES 不要用 VALUE

### 4. 事务

mysql 默认自动提交事务，执行一句提交一句

跳过，有需要再回头学

### 5. JDBC 工具类

- 问题一：注册驱动、获取连接等写了很多遍

- 问题二：每次都从数据库获取新的连接

  mysql是一个 TCP/IP 协议的网络程序，

  > - 每获取一次连接的成本很高，连接需要“三次握手”，断开需要“四次挥手”等过程
  >
  > - 每一个客户端都有单独的线程来维护它的通信，如果很多客户端同时连接mysql服务器就会造成：
  >
  >   > 1. mysql 的并发量就会有风险，如果太多服务器可能会挂，特别是获取完连接没有关闭
  >   > 2. 连接只是用一次太浪费资源了，我们希望能==重复利用连接对象==



Solution：

- 问题一：把注册驱动、获取连接等方法封装到一个工具类中
- 问题二：使用数据库连接池

##### 数据库连接池技术

- 先创建一个连接池pool，然后在池中放一些连接对象，程序可以直接在池中直接获取现有的对象
- 可以设置连接池的最大连接数，如果池中的所有连接都在使用，可以让“客户端”等待。不至于让服务器挂了。
- 创建连接池时，一开始是初始化少量的连接，等用户并发量上来后会增加连接数，直到增加到最大连接数
- 用完连接后，之前是用connection.close与服务器断开，现在从是还给连接池

##### Druid 数据库连接池

**Druid** 是阿里提供的数据库连接池，集 DBCP(Apache) 、C3P0、Proxool 优点于一身的数据库连接池。

1. 导入 <a href="https://repo1.maven.org/maven2/com/alibaba/druid/1.1.16">druid-1.1.16.jar </a>到当前工程的 library

2. 新建 Properties 设置连接参数

   ```
   为了获取连接，需设置：主机名、端口号、用户名、密码、驱动类名
   其它参数：初始化连接数、最多连接数...
   ```

   在 src 下创建一个 druid.properties文件。src就是sources类型，而配置文件应该是resources类型，所以我们在idea当中新建一个properties时，就要新建一个ResourceBundle类型的文件。配置如下：

   url 后本应加这句：`?rewriteBatchedStatements=true`，但加了`?serverTimezone=UTC`冲突了

   ```properties
   url=jdbc:mysql://localhost:3306/test?serverTimezone=UTC
   username=root
   password=12345c
   driverClassName=com.mysql.cj.jdbc.Driver
   initialSize=10
   maxActive=20
   maxWait=1000
   filters=wall
   ```

3. 创建连接池

   创建一个连接池，一个系统只创建一个

   ```java
   private static DataSource ds;
   ```

4. 提供一个可以从数据库连接池中取对象的方法

5. 提供一个关闭连接的方法

### 6. DAO : 数据访问接口和相关的类

DAO：Data Access Object

![项目分层](pic/%E9%A1%B9%E7%9B%AE%E5%88%86%E5%B1%82.png)

Big Data --Senior





# Java Web

BS架构：Browser/Server，有浏览器端/客户端 和服务器

CS架构：Client/Server，有安装包/客户端和服务器

![1583930684414](pic/1583930684414-1586334239634.png)

```mermaid
graph LR
	subgraph 客户端/Browser
	HTML/CSS/JS
	end
	
	subgraph 服务器端/Tomcat
	Servlet
	end
	
	HTML/CSS/JS --HTTP协议--> Servlet
	Servlet --HTTP协议--> HTML/CSS/JS

	
```

### 1. HTML

#### 1. 什么是HTML

1. HTML指的==超文本标记语言(Hyper Text Markup Language)==，是一种用来描述网页的语言。超文本指的是除了可以包含文字之外，还可以包含图片、链接、音乐、视频、程序等内容。

2. HTML网页的组成

   ![1583930847738](pic/1583930847738-1586334239634.png)

3. 常用的HTML标签

   1. html     根标记

   2. head     头标记

   3. body     体标记

   4. a           超链接

      ```html
      <!-- 超链接  href:可以指定应用内或者是应用外的任意地址 -->
       <a href="http://www.baidu.com">点我查看</a>
      ```

      ==相对路径：==

      ```html
      <!--   ../../ 表示上两级目录    -->
      <a href="../../target.html">hhh</a>
      ```

      ==target==属性：设置要跳转的页面在何处打开

   >_self : 默认，在当前页面打开
   >
   >_blank: 在新的标签页打开

      ==base== 可 设置全局的target属性

      ```html
   <base target="_blank">
      ```

      

   5. form     表单

      - 使用form标签创建一个表单

      - action属性：指定服务器地址（表单将被提交的地址）

      - method属性：指定表单的请求方式

        > get：默认值，发送一个GET请求，用户输入的数据通过地址栏传输
        >
        > post：发送一个POST请求，用户输入的数据通过请求体进行传输
        >
        > 区别：get的地址栏会显示name属性的键值对，post不会显示。但是按F12，点network监听一下，header里会显示用户和密码，http协议本身就是不安全的

      

      - 表单中的表达项用input表示，不同的表单项通过type指定，value属性指定按钮上显示的文字 
      - 用户输入数据通过name属性进行携带，并以键值对的形式发送到服务器，多个键值对之间用&分隔
      - 键值对如：`username=cxy&password=123456 `，name相当于键，用户输入的内容为值

      ```html
      <!-- 表单: 收集用户的信息，提交到后台服务器 -->
      <form action="success.html" method="POST">
          
          用户名：<input type="text" name="username"><br/>
          密码：<input type="password" name="password"><br/>
          <input type="submit" value="登录">
      
      </form>
      ```

   6. table     表格

      - tr   行

      - th   标题列  自带居中并加粗的效果

      - td   普通列

      - colspan 跨列合并单元格

      - rowspan 跨行合并单元格

      - align = “center” 居中

        ```html
        <table border = "lpx" align="center" width = "60" cellspacing = 0>
                <tr>
                    <th>ID</th>
                    <th>name</th>
                    <th>gender</th>
                    <th>age</th>
                    <th>birthday</th>
        
                </tr>
                <tr align="center">
                    <td align="center">100</td>
                    <td>cxy</td>
                    <!-- 跨行合并单元格 -->
                    <td rowspan="2">female</td>
                    <td>23</td>
                    <td>-</td>
                </tr>
        
                <tr align="center">
                    <td align="center">100</td>
                    <td>cc</td>
                    <td>female</td>
                    <td>23</td>
                    <td>-</td>
                </tr>
        
                <tr align="center">
                    <td align="center">100</td>
                    <td>wwh</td>
                    <td>male</td>
                    <!-- 跨列合并单元格 设置colspan属性 -->
                    <td colspan="2" align="center"> 22</td>
                </tr>
        
            </table>
        ```

### 2. CSS

- 整个标签

  > 标签选择器

- 标签里面设置属性

  > id选择器
  >
  > 类选择器

- 分组选择器

  > 为不同类别的选择器设置相同的属性

```css
<head>
    <style type="text/css">
    /*标签选择器*/
    h1{
        color: yellow;
    }
    h2{
        background-color: antiquewhite;
    }

    /*id选择器
      格式：#id属性值
    */
    #p1{
        color: aqua;
    }

    /*类选择器
      格式：.class属性值
    */
    .p2{
        color: yellowgreen;
    }

    /*分组：将各个选择器用逗号分隔*/
    #p1,.p2{
        font-size: 22px;
    }
    </style>
</head>
```

颜色的表示方式：

1. 英文单词：red

2. rgb 值 ：rgb(250,0,0)

3. 使用 16 进制数：#FF0000  不区分大小写，从左到右两位一组，分别表示 R G B

    

### 3. Web

 [01_JavaWeb.html](ref/01_JavaWeb.html) 

#### web服务器

服务器主要用来接收或响应客户端发来的请求，当前使用最广的服务器：==Tomcat==

修改端口号：修改安装目录下的 `conf/service.xml` 里的启动端口号8080

#### 第一个web动态工程

[IDEA创建web工程](<https://www.cnblogs.com/wfhking/p/9395774.html>)

1. 运行web工程会自动展示此页面，工作空间内的此页面会被自动copy到服务器，然后在服务器中访问web/index.html页面

2. web/WEB-INF下需要自己建两个文件夹：**classes**（设置输出路径到此处,运行工程后工作空间内的类会加载到此处）, **lib**（设置为 dependency 后，用来放工程jar包）

3. 工程中服务器的工作路径选择 tomcat 的源路径。Eclipse中==web 目录会被 copy 到 tomcat 的 webapps下，同时把 web 改为工程名==。IDEA 中需自己设置路径，即 project structure 中 artifact 的目录。

4. index页面中按 F12，刷新看index的Headers 

   报文：分为 行、头、体

   > 浏览器发给服务器的是 ==请求报文==，分为请求行、请求头、请求体
   >
   > ```
   > //请求头
   > Request Headers
   > //请求行
   > GET /Web_tomcat_war_exploded/ HTTP/1.1
   > //请求体
   > Host: localhost:8080
   > Connection: keep-alive
   > Cache-Control: max-age=0
   > Upgrade-Insecure-Requests: 1
   > User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.149 Safari/537.36
   > Sec-Fetch-Dest: document
   > Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
   > Sec-Fetch-Site: none
   > Sec-Fetch-Mode: navigate
   > Sec-Fetch-User: ?1
   > Accept-Encoding: gzip, deflate, br
   > Accept-Language: zh-CN,zh;q=0.9
   > Cookie: Idea-c3466856=bdab302f-9076-4c60-a7e9-778b2a6ffd03
   > If-None-Match: W/"714-1584880762014"
   > If-Modified-Since: Sun, 22 Mar 2020 12:39:22 GMT
   > ```
   >
   > 服务器发给浏览器的是 ==响应报文==，分为响应行、响应头、响应体
   >
   > ```
   > //响应头
   > Response Headers
   > //响应行
   > HTTP/1.1 200
   > //响应体
   > Date: Sun, 22 Mar 2020 12:43:30 GMT
   > Accept-Ranges: bytes
   > ETag: W/"714-1584880762014"
   > Last-Modified: Sun, 22 Mar 2020 12:39:22 GMT
   > Content-Type: text/html
   > Content-Length: 714
   > ```

#### 3.1 登录功能实现—LoginServlet

1)        Servlet  

2)        Request请求对象

3)        Response响应对象

##### 1 什么是Servlet

1. Servlet是Sun公司制定的一套技术标准，包含与Web应用相关的一系列接口，是Web应用实现方式的<u>宏观解决方案</u>。而具体的 ==Servlet 容器（Tomcat）负责提供标准的实现==。

2. Servlet作为服务器端的一个组件，它的本意是“服务器端的小程序”（==Tomcat中会有多个Servlet，每一个Servlet都负责处理一件事，如登录、注册==）。Servlet的实例对象由Servlet容器负责创建；Servlet的方法由容器在特定情况下调用；Servlet容器会在Web应用卸载时销毁Servlet对象的实例。

   ```mermaid
   graph LR
   
   	Cient --HTTP--> Servlet_登录
   	Servlet_登录 --HTTP--> Cient
   	subgraph Tomcat
   	Servlet_注册
   	Servlet_登录
   	Servlet_忘记密码
   	...
   	end
   ```

3. 简单可以理解为  ==Servlet就是用来处理客户端的请求的== 

##### 2 Servlet开发规则

新建一个Servlet

##### 3 Servlet类的相关方法

- doGet：处理客户端的get方式的请求

- doPost：处理客户端的post方式的请求

- service：根据具体的请求方式去调用对应的doGet、doPost 方法

  >  ①      在Servlet的顶层实现中，在service方法中调用的具体的doGet或者是doPost
  >
  >  ②      在实际开发Servlet的过程中，可以选择重写doGet以及doPost  或者 直接重写service方法来处理请求。

#####4 Servlet在web.xml中的配置

```xml
<!--注册Servlet-->
<servlet>
  <!-- 给Servlet取名，一般写类名.取的名字前后必须一致-->
  <servlet-name>helloServlet</servlet-name>
  <!-- 配置Servlet实现类的全类名，Servlet容器会利用反射帮我们创建对象-->
  <servlet-class>com.atguigu.servlet.helloServlet</servlet-class>
</servlet>
    
<!--映射Servlet。如果用户发送多个请求，需要知道是谁发的-->
<servlet-mapping>
  <servlet-name>helloServlet</servlet-name>
  <!--配置映射的请求地址,在浏览器的地址栏输入MyFirstServlet的时候才发起请求-->
  <url-pattern>/MyFirstServlet</url-pattern>
</servlet-mapping>
```

Servlet 3.0之后可以在Servlet中使用注解直接配置URL。需要在Servlet中导入`import javax.servlet.annotation.WebServlet;` 。然后使用

```java
@WebServlet(name = "AutoServlet",urlPatterns = "/AutoServlet")
//注意urlPatterns那里要写/  
//也可以如下：
@WebServlet("/AutoServlet")
```

==name  和 urlPatterns 对应 web.xml 中的 <url-name> 和 <url-pattern>== 

就可以直接配置了，然后通过所输入的URL可以直接访问到。

##### 5 request 和 response 的使用

==request== 的作用

- 获取请求参数

- 获取项目虚拟路径

- 转发

  ![img](pic/转发.png)

==response== 的作用

- 给浏览器响应一个字符串或一个页面
- 重定向

==转发和重定向的区别：==

1. 转发只发一次请求，即AutoServlet。重定向发了2次请求：AutoServlet 和 success.html
2. 转发浏览器地址栏无变化，重定向有变化
3. 转发可以访问WEB-INF目录下的资源，==重定向不可以访问WEB-INF目录下的资源==
4. 转发可以共享request域中的内容，重定向不可以

##### 6. 登录之获取链接

```mermaid
graph LR
	subgraph 前端
	表单
	end
	
	subgraph 服务器
	Servlet
	end
	
	subgraph 数据库
	MySql
	end
	
	表单 --> Servlet
	Servlet --> 表单
	
	Servlet --JDBC--> MySql
```

##### 7. 绝对路径与相对路径

因为在login中使用 相对路径 ../LoginServlet 导致二次登录时又到了上级目录，所以使用绝对路径来解决此问题

绝对路径

- 以 ==/ 开头的路径即为绝对路径==     / 代表的意义：

  > 1. 如果地址由浏览器解析， / 代表： http://localhost:8080/。如：
  >
  >    > - html标签中的路径，如：
  >    >
  >    >   > - a 标签中的 href 属性中的路径
  >    >   > - form 标签中的 action 属性中的路径等
  >    >
  >    > - 重定向中的路径
  >    >
  >    >   
  >
  > 2. 如果由服务器解析， / 代表： http://localhost:8080/Web_Exercise_war_exploded/ (即服务器中项目的地址。注意==不要随便改tomcat自动创建的URL地址==，如：http://localhost:8080/Web_Exercise_war_exploded/，不要强行去掉_war_exploded，就算把artifact中的路径一起改也不行），如：
  >
  >    > - web.xml中url-pattern标签中的路径
  >    > - 转发中的路径
  >
  > 

- ==head 里==的 base 标签中的href可以将相对路径变为绝对路径，因为它会加到body里href属性里的地址前面

  ```html
   	<head>
   	  <meta charset="UTF-8">
   	  <title>Insert title here</title>   
   	  <base href="http://localhost:8080/Web_Exercise_war_exploded/"></head>
  ```

index.html , login.html, login_success.html , LoginServlet.java 中的路径也需改为绝对路径

#### 3.2 登录页面中的错误提示

- JSP页面
- EL 表达式
- js 的简单应用

##### 1. JSP

- JSP全称Java Server Pages，顾名思义就是**运行在java服务器中的页面**，也就是在我们JavaWeb中的动态页面，其==本质就是一个Servlet==。

- 其本身是一个动态网页技术标准，它的主要构成有HTML网页代码、Java代码片段、JSP标签几部分组成，后缀是 .jsp

- 相比于Servlet，JSP更加善于处理显示页面，而Servlet跟擅长处理业务逻辑，两种技术各有专长，所以一般我们会将Servlet和JSP结合使用，Servlet负责业务，JSP负责显示。

- 一般情况下， 都是Servlet处理完的数据，转发到JSP，JSP负责显示数据的工作

- JSP的基本语法:

- 本质上就是一个Servlet

  

  **JSP基本语法**

- 1. ==JSP脚本片段== 

     作用：用来在里面写Java代码

     ```jsp
     <!-- 1.JSP脚本片段
     		作用：用来在里面写Java代码
     	 -->
     	 <%
     	 	for(int i = 0 ; i < 5 ; i ++){
     	 		//out.print("今天天气好晴朗，处处好风光！");
     	 %>		
     	 <h2>今天天气好晴朗，处处好风光！</h2>
     	 <%
     	 	}
     	 %>
     ```

  2. ==JSP表达式==

     - - 作用：用来输出对象

     - - ```jsp
         <%="我是通过JSP表达式输出的" %>
         ```

  3. JSP 的隐含对象

     - out（JspWriter）：相当于response.getWriter()获取的对象，用于在页面中显示信息。
     - config（ServletConfig）：对应Servlet中的ServletConfig对象。
     - page（Object）：对应当前Servlet对象，实际上就是this。
     - ==pageContext==（PageContext）：当前页面的上下文，也是一个域对象。
     - exception（Throwable）：错误页面中异常对象
     - ==request==（HttpServletRequest）：HttpServletRequest对象
     - response（HttpServletResponse）：HttpServletResponse对象
     - ==application==（ServletContext）：ServletContext对象
     - ==session==（HttpSession）：HttpSession对象

     只需要掌握高亮的4个域对象

  4. ==JSP 的四个域对象==

     ==这4个域对象有不同的生命周期==

     - page域

       > 范围：当前页面（页面关掉 对象消失）
       > ==对应的域对象==：即用来调用域内方法的对象
       >
       > > page对应的域对象 ： pageContext
       >
       > 域对象的类型：PageContext

     - request域

       > 范围：当前请求（一次请求，转发还是一次请求，重定向是新的请求）
       > 对应的域对象：request
       > 域对象的类型：HttpServletRequest

     - session域

       > 范围：当前会话（一次会话，只要浏览器不关闭都可以拿到它的请求）
       > 对应的域对象：session
       > 域对象的类型：HttpSession

     - application域

       >范围：当前 Web 应用（服务器关掉应用停止）
       >对应的域对象：application
       >域对象的类型：ServletContext

     

     四个域对象都以下三个方法：

     - void setAttribute(String key , Object value)
     - Object getAttribute(String key)
     - void removeAttribute(String key)

     ```jsp
     <%
     	 	pageContext.setAttribute("pageKey", "pageValue");
     	 	request.setAttribute("reqKey", "reqValue");
     	 	session.setAttribute("sessKey", "sessValue");
     	 	application.setAttribute("appKey", "appValue");
     %>
     	 <h1>在当前页面中获取四个域中的属性值</h1>
     	 page域中的属性值：<%=pageContext.getAttribute("pageKey") %><br>
     	 request域中的属性值：<%=request.getAttribute("reqKey") %><br>
     	 session域中的属性值：<%=session.getAttribute("sessKey") %><br>
     	 application域中的属性值：<%=application.getAttribute("appKey") %><br>
     ```

     

     四个域对象的使用规则：能用小的就不用大的

     

**登录失败后添加错误提示**

在LoginServlet 判断用户名密码的时候 加入

```java
request.setAttribute("msg","用户名或密码不正确");
```

然后在登录界面中：

```jsp
用户名称：<input type="text" name=username><span style="color: red"><%= request.getAttribute("msg") == null ? "": request.getAttribute("msg")%></span> 
```

##### 2. EL（Expression Language）

- 格式：==${表达式}==
- 作用：主要用来输出域对象中的属性值

1. EL是JSP内置的表达式语言，用以访问页面的上下文以及不同作用域中的对象 ，==输出对象属性的值==，或执行简单的运算或判断操作。EL在得到某个数据时，会自动进行数据类型的转换。
2. **EL** 表达式用于代替JSP表达式 `<%= %>` 在页面中做输出操作。
3. EL表达式仅仅用来读取数据，而不能对数据进行修改。
4. 使用EL表达式输出数据时，**如果有则输出数据，如果为null则什么也不输出。**
5. EL 表达式的语法

> EL表达式查询的规则：
>
> > 1. 先从page域中开始查找，找到后直接返回，不再向其他域中查找，如果找不到再去request域中查找，以此类推...
> >
> > 2. 如果在application域中仍找不到则返回空串
> >
> > 3. ==EL 提供了四个Scope对象==，用来精确获取指定域中的属性值。优先级由高到低:
> >
> >    > - pageScope
> >    >
> >    >   > 获取page域中的属性值
> >    >
> >    > - requestScope
> >    >
> >    >   > 获取request域中的属性值
> >    >
> >    > - sessionScope
> >    >
> >    >   > 获取session域中的属性值
> >    >
> >    > - applicationScope	
> >    >
> >    >   > 获取application域中的属性值
>
> > ```jsp
> > <%
> > //创建Employee对象
> > Employee employee = new Employee(1,"吴秀波",new Department(1001,"出轨门"));
> > //将employe对象放到page域中
> > pageContext.setAttribute("star", employee);
> > %>
> > 
> > 通过EL表达式输出Employee对象的lastName：${pageScope.star.lastName }<br>
> > 通过EL表达式输出Employee对象的dept属性的name属性值：${pageScope.star.dept.name }<br>
> > 
> > 通过EL表达式输出Employee类中getOutName方法的返回值：${pageScope.star.outName }<br>
> > 
> > star.后面调用的是employee对象里的get的方法，名字是将get方法去掉get，首字母变成小写
> > ```

##### 3. JavaScript

1. 在1995年时，由[Netscape](http://baike.baidu.com/view/153922.htm)公司的[Brendan 	Eich](http://baike.baidu.com/view/2135520.htm)，在[网景导航者](http://baike.baidu.com/view/1350596.htm)浏览器上首次设计实现而成。[Netscape](http://baike.baidu.com/view/153922.htm)在最初将其脚本语言命名为[LiveScript](http://baike.baidu.com/view/2373233.htm)，因为[Netscape](http://baike.baidu.com/view/153922.htm)与[Sun](http://baike.baidu.com/subview/24856/10322735.htm)合作，网景公司管理层希望它外观看起来像[Java](http://baike.baidu.com/subview/29/12654100.htm)，因此取名为JavaScript。

2. 特性

   > - 脚本语言。JavaScript是一种解释型的脚本语言,C、C++、Java等语言先编译后执行,	而JavaScript是在程序的运行过程中逐行进行解释。
   > - 基于对象。JavaScript是一种基于对象的脚本语言,它不仅可以创建对象,也能使用现有的对象。
   > - 简单。JavaScript语言中采用的是弱类型的变量类型,对使用的数据类型未做出严格的要求,是基于Java基本语句和控制的脚本语言。
   > - 动态性。JavaScript是一种采用事件驱动的脚本语言,它不需要经过Web服务器就可以对用户的输入做出响应。
   > - 跨平台性。JavaScript脚本语言不依赖于操作系统,仅需要浏览器的支持。因此一个JavaScript脚本在编写后可以带到任意机器上使用,前提是机器上的浏览器支	持JavaScript脚本语言,目前JavaScript已被大多数的浏览器所支持

3. 编写位置

   1.  编写到HTML中<script>标签中

       ```html
       <head>
         <script type="text/javascript">
           
         </script>
       </head>
       ```

   2.  写在外部的 .js 文件中。然后通过script标签引入

   ```html
   <script type="text/javascript" src="script.js"></script>
   ```

4. JavaScript的事件驱动

   - 用户事件：用户操作，例如单击、鼠标移入、鼠标移出等

   - 系统事件：由系统触发的事件，例如文档加载完成

   - 常用的事件

     > onload：当整个文档都加载完成之后再执行函数中的内容
     >
     > onclick：给按钮对象绑定单击事件
     >
     > onblur
     >
     > onfocus
     >
     > onmouseover
     >
     > onmouseout

5. ==BOM==

   - Borwser Object Model 浏览器对象模型
   - 浏览器对象模型提供了独立于内容的、可以与浏览器窗口进行互动的对象结构。BOM由多个对象组成，其中代表浏览器窗口的Window对象是BOM的顶层对象，其他对象都是该对象的子对象
   - 常用的对象(window的子对象)

    document  history    location    screen   navigator    frames

6. ==DOM==

   - Document Object Model 文档对象模型

   - document对象: window对象的一个属性，代表当前HTML文档，包含了整个文档的树形结构。获	取document对象的本质方法是：window.document，而“window.”可以省略

   - DOM树

     ![image-20200324215533469](pic/DOM树.png)

   - 元素查询

     

     | 功能               | API                                     | 返回值             |
     | ------------------ | --------------------------------------- | ------------------ |
     | 根据id值查询       | document.getElementById(“id值”)         | 一个具体的元素节点 |
     | 根据标签名查询     | document.getElementsByTagName(“标签名”) | 元素节点数组       |
     | 根据name属性值查询 | document.getElementsByName(“name值”)    | 元素节点数组       |



#### 3.3 注册

##### 1 jQuery

1. jQuery是为了==简化==JavaScript开发而生的一个小型的框架，jQuery和 \$ 是相等的，我们==通常使用 \$ 代替 jQuery 这个单词==

   ```javascript
   <script type="text/javascript" src="script/jquery-1.7.2.js"></script>
   <script type="text/javascript">
     			//当整个文档都加载完成之后再执行函数中的内容
   
   //在JavaScript中
   window.onload = function(){
     //1.获取按钮对象
     var btnEle = document.getElementById("btnId");
     //2.给按钮对象绑定单击事件
     btnEle.onclick = function(){
     //3.弹出提示框
     alert("Hello JavaScript!");
     };
   };
   
   //在jQuery中
   $(function(){
   		//获取按钮对象并给它绑定单击事件
   		$("#btnId").click(function(){
   			//弹出提示框
   			alert("Hello jQuery!");
   		});
   });
   </script>
   ```

```
   

   
   - 基本选择器
   
  > - ID选择器 ：`$("#id属性值")`
     > - 类选择器：`$(".class属性值")`
  > - 标签选择器：$("html标签")
   
   - 常用的方法
   
     > 1. attr()
     >
     >    - 获取或设置标签的属性值
     >    - 对象.attr("属性名")：获取属性值
     >    - 对象.attr("属性名","属性值")：设置属性值
     >
     > 2. text()和html()方法
     >
     >    - 获取或设置成对出现的标签中的文本值
     >
     >    - 对象.text()：获取文本值
     >
     >    - 对象.text("新值")：设置文本值
     >
     >    - html()方法与text()方法的唯一区别是html方法可以解析html标签
     >
     >      详见：Java_Web/day03/Web_Ex/项目下的 login.js
     >
     > 3. val()
     >
     >    - 获取或设置input标签的value属性值
     >
     >    - 对象.val()：获取value属性值
     >
     >    - 对象.val("新值")：设置value属性值
     >
     >      详见：Java_Web/day03/Web_Ex/项目下的 login.js
     >
     > 4. 事件
     >
     >    - click()：单击事件
     >    - change()：内容改变的事件
     >
     > 5. 正则表达式
     >
     >    ```javascript
     >    $(function(){
     >      //给提交按钮绑定单击事件
     >      $("#sub").click(function(){
     >    	//获取用户输入的用户名
     >    	var username = $("#username").val();
     >    	//设置一个验证用户名是否符合规则的正则表达式
     >    	//var userReg = /a/;//  /a/表示只要用户名内有a就可以提交表单
     >      // ^设置开头的格式限制，_-表示允许_和-开头{}内的内容限制用户名长度
     >    	var userReg = /^[a-zA-Z0-9_-]{3,6}$/;
     >    	//验证用户名是否符合规则
     >    	var flag = userReg.test(username);
     >    	if(!flag){
     >    		alert("请输入3-6位的字母、数字、下划线或减号的用户名！");
     >    		return false;
     >    	}
  >      });
     >    });
     >    ```
   
   

#####  2. Ajax

- AJAX 是 Asynchronous JavaScript And XML 的简称。直译为，异步的 JS 和XML。
- AJAX的实际意义是，不发生页面跳转、异步载入内容并改写页面内容的技术。
- AJAX也可以简单的理解为通过 JS 向服务器发送请求。

1. 同步处理

​	AJAX出现之前，我们访问互联网时一般都是同步请求，也就是当我们通过一个页面向	服务器发送一个请求时，在服务器响应结束之前，我们的整个页面是不能操作的，也就	是直观上来看他是卡主不动的。

​	这就带来了非常糟糕的用户体验。首先，同步请求时，用户只能等待服务器的响应，而	不能做任何操作。其次，如果请求时间过长可能会给用户一个卡死的感觉。最后，同步	请求的最大缺点就是即使整个页面中只有一小部分内容发生改变我们也要刷新整个页	面。

2. 异步处理

 而异步处理指的是我们在浏览网页的同时，通过AJAX向服务器发送请求，发送请求的过程中我们浏览网页的行为并不会收到任何影响，甚至主观上感知不到在向服务器发送请求。当服务器正常响应请求后，响应信息会直接发送到AJAX中，AJAX可以根据服务器响应的内容做一些操作。

 使用AJAX的异步请求基本上完美的解决了同步请求带来的问题。首先，发送请求时不会影响到用户的正常访问。其次，即使请求时间过长，用户不会有任何感知。最后，AJAX可以根据服务器的响应信息局部的修改页面，而不需要整个页面刷新。

**通过 $.ajax 发送 Ajax请求**

​```javascript
$("#btnId").click(function(){
	//通过$.ajax()方法发送Ajax请求
	/*
		url：必须的。用来设置请求地址
		type：可选的。用来设置发送请求的请求方式，默认是get
		data：可选的。用来设置请求参数
		success：可选的。用来设置回调函数，响应成功之后系统会自动调用该函数，
				响应数据会以参数的形式传入到该函数中
		dataType：可选的。用来设置响应数据的类型，默认是text，还可以设置xml、json等		
	*/
	$.ajax({
		url:"${pageContext.request.contextPath }/AjaxServlet",
		type:"get",
		data:"username=admin&password=123456",
		success:function(res){
			//将响应信息设置到span标签中
			$("#res").text(res);
		},
		dataType:"text"
	});
});
```

**通过 \$.get() 或 \$.post() 发送Ajax请求**

get 和 post 指请求的 method，post请求用\$.post

```javascript
$("#btnId2").click(function(){
	//通过$.get/post()方法发送Ajax请求
	/*
		$.get(url, [data], [callback], [type])
			url：必须的。用来设置请求地址
			data：可选的。用来设置请求参数
			callback：可选的。用来设置一个回调函数，响应成功之后系统会自动调用该函数，
					响应数据会以参数的形式传入到该函数中
			type：可选的。用来设置响应数据的类型		
	*/
	//设置请求地址
	var url = "${pageContext.request.contextPath }/AjaxServlet";
	//设置请求参数
	var params = "username=admin&password=666666";
// 			$.get(url,params,function(res){
// 				//将响应数据设置到span标签中
// 				$("#res2").text(res);
// 			},"text");
	//通过$.post()发送一个post请求
	$.post(url);
});
```

##### 3. JSTL

- JSP 的标准标签库，使用它需要导入以下jar包

  > jstl.jar
  >
  > standard.jar

- 使用c标签需要导入核心标签库

  ```javascript
  <%@ taglib uri=*"http://java.sun.com/jsp/jstl/core"* prefix=*"c"* %> 
  ```

- if 标签

  ```javascript
   	 <%
  	 	int age = 86;
  	 	pageContext.setAttribute("age", age);
  	 %>
  	 <c:if test="${age < 18 }">
  	 	禁止未成年人入内！
  	 </c:if>
  	  <c:if test="${age > 18 }">
  	 	请尽情浏览，注意身体！！！
  	 </c:if>
  	 <%
  ```

- forEach 标签

 ```javascript
<%
  List<String> list = new ArrayList();
 	 	list.add("吉沢明步");
 	 	list.add("蓝泽润");
 	 	list.add("京香JULIA");
 	 	list.add("潘金莲");
 	 	list.add("文章");
 	 	list.add("白百何");
 	 	list.add("李小璐");
 	 	list.add("林丹");
 	 	list.add("吴秀波");
  //将list放到page域中
  pageContext.setAttribute("stars", list);
%>
<hr>
<!-- forEach标签：相当于Java中的for循环
    items属性：接收一个要遍历的集合
    var属性：设置一个遍历接收遍历到的值，同时会以变量值为key将遍历到的值放到page域中
 -->
<c:forEach items="${stars }" var="star">
  <a href="#">${pageScope.star }</a><br>
</c:forEach>
<!--
 ```



- empty运算符

- > 用来判断一个字符串或一个集合是否为空
  >
  > ```javascript
  > empty运算符：主要用来判断一个字符串或一个集合是否为空
  > -->
  > <c:if test="${empty pageScope.stars }">
  > 世界很美好，没有人乱搞！！！
  > </c:if>
  > ```

#### 3.4 登录功能实现-登录成功跳转主页面

- Session会话 
- Cookie  
- [JSTL](#3. JSTL)

##### 1. Cookie

**Cookie的运行原理**

​      1.第一次向服务器发送请求时在服务器端创建一个Cookie对象

​      2.将Cookie对象发送给浏览器

​      3.以后浏览器再发请求就会携带着该Coolie对象

​      4.服务器通过不同的Cookie来区别不同的用户

1. HTTP是==无状态协议==，服务器不能记录浏览器的访问状态，也就是说==服务器不能区分中两次请求是否由一个客户端发出==。这样的设计严重阻碍的Web程序的设计。如：在我们进行网购时，买了一条裤子，又买了一个手机。由于http协议是无状态的，如果不通过其他手段，服务器是不能知道用户到底买了什么。而Cookie就是解决方案之一。

2. Cookie实际上就是服务器==保存在浏览器上==的一段信息。浏览器有了Cookie之后，每次向服务器发送请求时都会同时将该信息发送给服务器，服务器收到请求后，就可以根据该信息处理请求。

    

 **Cookie的用途**

1. 网上商城购物车
2. 用户登录状态的保持

**Cookie的限制性**

1. Cookie作为请求或响应报文发送，无形中增加了网络流量

2. Cookie是明文传送的安全性差

3. 各个浏览器对Cookie有限制，使用上有局限

    

##### 2. session

**Session的运行原理：**

1. 第一次向服务器发送请求时==在服务器端创建一个Session对象==，该对象有一个全球唯一的ID
2. 在创建Session对象的同时会创建一个特殊的Cookie对象，该Cookie对象的名字是一个固定值：==JSESSIONID==， 该Cookie对象的==值==就是Session对象的==ID==值，并且将该Cookie对象发送给浏览器
3. 以后浏览器再发送请求就会携带着这个特殊的Cookie对象
4. 服务器获取Cookie对象的值之后寻找与之对应的Session对象，以此来区分不同的用户 



##### 3.5 完成注销功能及钝化和活化

==注销==：使session对象失效

==钝化==：服务器关闭时，session及session里的用户从内存持久化到硬盘，叫钝化

==活化==：服务器再启动时，会从硬盘反序列化到内存，叫活化

##### 3.6 主页面访问权限控制

**过滤器**

    1) 对于WEB应用来说，过滤器是一个驻留在服务器中的WEB组件，他可以截取客户端和WEB资源之间的请求和响应信息。WEB资源可能包括Servlet、JSP、HTML页面等
    2) 当服务器收到特定的请求后，会先将请求交给过滤器，程序员可以在过滤器中对请求信息进行读取修改等操作，然后将请求信息再发送给目标资源。目标资源作出响应后，服务器会再次将响应转交给过滤器，在过滤器中同样可以对响应信息做一些操作，然后再将响应发送给服务器。
    3) 也就是说过滤器可以在WEB资源收到请求之前，浏览器收到响应之前，对请求和响应信息做一些相应的操作。
    4) 在一个WEB应用中可以部署多个过滤器，多个过滤器就组成了一个过滤器链，请求和响应必须在经过多个过滤器后才能到达目标

**过滤器的使用**
    1) 通过实现Filter接口完成过滤器的开发

```java
//filterSevelet设置，urlPatterns的值表示拦截地址，也可以用 servletNames
//拦截路径发出请求时，filter将决定是否拦截
@WebFilter(filterName = "HelloFilter",urlPatterns = "/index.jsp")
//放行请求,不写此句则表示拦截
chain.doFilter(req, resp);
```

- 作用：用来==拦截用户的请求==，但是Filter只拦截请求==不拦截响应==

- 我们还可以为同一个资源设置多个过滤器，多个过滤器的拦截顺序由web.xml中的filter-mapping　标签对，在前的先拦截，在后的后拦截。如果不设置，则按filter创建的先后顺序，后创建的优先。

  ![filter](pic/filter.png)

- 以拦截index.jsp页面为例创建两个拦截器

- - HelloFilter
  - HelloFIlter2

##### 3.5 在线人数统计

**监听器**

- Lisener 监听器用来监听ServletRequest、HttpSession、ServletContext对象的生命周期和三个域中的属性变化

- 分类

  > 1. 1. 生命周期 
  >    2. 数据绑定			

- 掌握==ServletContext==的生命周期监听器

- > ServletContextListener
  >
  > > - 通过该接口创建的监听器服务器已启动该对象就被创建
  > >
  > > - 服务器关闭该对象就销毁

- - 

# Maven

#### XML

1. XML--可扩展标记语言eXtensible Markup Language
2. 由W3C组织发布，目前推荐遵守的是W3C组织于2000年发布的XML1.0规范
3. XML的使命，就是以一个统一的格式，组织有关系的数据，为不同平台下的应用程序服务
4. XML用来==传输和存储数据==，HTML用来显示数据
5. XML没有预定义标签，均为==自定义标签==

##### xml 用途

1. 配置文件

   > -  JavaWeb 中的 web.xml
   > -  C3P0中的c3p0-config.xml

2. 数据交换格式

   > - ==Ajax==
   > - WebService

3. 数据存储

   保存关系型数据

   

##### xml 语法

1. XML文档组成

   > - XML声明
   >
   >   > 1. version属性指定XML版本，固定值是1.0
   >   > 2. encoding指定的字符集，是告诉解析器使用什么字符集进行解码，而编码是由文本		编辑器决定的
   >
   > - CDATA区
   >
   >   > 1. 当XML文档中需要写一些程序代码、SQL语句或其他不希望XML解析器进行解析的内容时，就可以写在CDATA区中
   >   >
   >   > 2. XML解析器会将CDATA区中的内容原封不动的输出
   >   >
   >   >    > CDATA区的定义格式：`<![CDATA[…]]>`

2. 语法规则

   - XML声明要么不写，要写就写在第一行，并且前面没有任何其他字符
   - 只能有一个根标签
   - 标签必须正确结束
   - 标签不能交叉嵌    
   - 严格区分大小写
   - 属性必须有值，且必须加引号
   - 标签不能以数字开头
   - 注释不能嵌套

3. xml解析

   >- XML解析是指通过解析器读取XML文档，解释语法，并将文档转化成对象
   >- 常用的解析方式
   >
   >> DOM（Document Object Model）
   >>
   >> SAX（Simple API for XML）
   >
   >- DOM 和SAX解析的对比
   >
   > ![Dom_SAX](pic/Dom_SAX.png)
   >
   >- Dom4j解析示例
   >
   > ```java
   > 				//创建解析对象
   >         SAXReader saxReader = new SAXReader();
   > 
   >         //解析xml文档
   >         Document document = saxReader.read("students.xml");
   > 
   >         //获取根标签student
   >         Element rootElement = document.getRootElement();
   > 
   >         //获取所有的student标签
   >         List<Element> stus = rootElement.elements("student");
   > ```

   

#### JSON

1. AJAX一开始使用的时XML的数据格式，XML的数据格式非常简单清晰，容易编写，但是由于XML中包含了过多的标签，以及十分复杂的结构，解析起来也相对复杂，所以目前来讲，AJAX中已经几乎不使用XML来发送数据了。取而代之的是一项新的技术JSON。
2. JSON是 **JavaScript Object Notation** 的缩写，是JS提供的一种数据交换格式。
3. JSON对象本质上就是一个JS对象，但是这个对象比较特殊，它可以直接转换为字符串，在不同语言中进行传递，通过工具又可以转换为其他语言中的对象。
4. 如下一个JSON对象：

```json
1 {“name”:”sunwukong” , ”age”:18 , ”address”:”beijing” }
2 这个对象中有三个属性name、age和address
3 如果将该对象使用单引号引起了，那么他就变成了一个字符串
4 ‘{“name”:”sunwukong” , ”age”:18 , ”address”:”beijing” }’
5 变成字符串后有一个好处，就是可以在不同语言之间传递。
6 比如，将JSON作为一个字符串发送给Servlet，在Java中就可以把JSON字符串转换为一个Java对象。
```

##### JSON 的数据类型

1. 字符串

   用“”表示，不能使用单引号。

2. 数字 ： 123.4

3. 布尔值：true、false

4. null

5. 对象：{“name”:”sunwukong”, ”age”:18}

6. 数组：[1,”str”,true]

##### JS中操作JSON

1. 创建JSON对象

   ```json
   //对象用{}括起来，属性名必须使用""括起来；属性名和属性值之间使用冒号分隔；多个属性之间使用逗号分隔
   var jsonObj = {"name":"孙悟空","age":520};
   ```

2. 创建JSON数组

   ```json
   var jsonArray = ["猪八戒",1000,false,null,jsonObj];
   ```

3. JSON对象转换为JSON字符串

   ```json
   var objToStr = JSON.stringify(jsonObj);
   ```

4. 声明一个JSON字符串

   ```json
   var jsonStr = '{"name":"白骨精","age":18}';
   ```

5. 将JSON字符串转换为JSON对象

   ```json
   var strToObj = JSON.parse(jsonStr);
   ```



##### 在Java中操作JSON

1. 在Java中可以从文件中读取JSON字符串，也可以是客户端发送的JSON字符串，所以第一个问题，我们先来看如何将一个JSON字符串转换成一个Java对象。

2. 首先解析JSON字符串我们需要导入第三方的工具，目前主流的解析JSON的工具大概有三种json-lib、jackson、gson。三种解析工具相比较json-lib的使用复杂，且效率较差。而Jackson和gson解析效率较高。使用简单，这里我们以gson为例讲解。

3. Gson是Google公司出品的解析JSON工具，使用简单，解析性能好。

4. Gson中解析JSON的核心是Gson的类，解析操作都是通过该类实例进行。

5. JSON字符串转换为对象

   ```json
   String json = "{\"name\":\"张三\",\"age\":18}";
   Gson gson = new Gson();
   //转换为集合
   Map<String,Object> stuMap = gson.fromJson(json, Map.class);
   //如果编写了相应的类也可以转换为指定对象
   Student fromJson = gson.fromJson(json, Student.class);
   ```

6. 对象转换为JSON字符串

   ```json
   Student stu = new Student("李四", 23);
   Gson gson = new Gson();
   //{"name":"李四","age":23}
   String json = gson.toJson(stu);
   		
   Map<String , Object> map = new HashMap<String, Object>();
   map.put("name", "孙悟空");
   map.put("age", 30);
   //{"age":30,"name":"孙悟空"}
   String json2 = gson.toJson(map);
   List<Student> list = new ArrayList<Student>();
   list.add(new Student("八戒", 18));
   list.add(new Student("沙僧", 28));
   list.add(new Student("唐僧", 38));
   //[{"name":"八戒","age":18},{"name":"沙僧","age":28},
   {"name":"唐僧","age":38}]
   String json3 = gson.toJson(list);		
        // 如果将一个数组格式的json字符串转换成java对象需要用到
        //Gson提供的一个匿名内部类： TypeToken
   	TypeToken tk= new TypeToken<List<User>>(){};
   	List<User> list2 = gson.fromJson(json,tk.getType());
   	System.out.println(list2.get(0));
   ```

   


#### 第一个Maven工程

1. 创建约定的目录结构

Hello

> - src
>
> > - main
> >
> > > - java
> > >
> > > - resources
> >
> > - test
> >
> > > - java
> > >
> > > - resources
>
> - pom.xml

```
main目录用于存放主程序。
test目录用于存放测试程序。
java目录用于存放源代码文件。
resources目录用于存放配置文件和资源文件。
```

2. 创建Maven的核心配置文件pom.xml

   ```pom
   <?xml version="1.0" ?>
   <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
   	<modelVersion>4.0.0</modelVersion>
   
   	<groupId>com.atguigu.maven</groupId>
   	<artifactId>Hello</artifactId>
   	<version>0.0.1-SNAPSHOT</version>
   
   	<name>Hello</name>
   	  
   	<dependencies>
   		<dependency>
   			<groupId>junit</groupId>
   			<artifactId>junit</artifactId>
   			<version>4.0</version>
   			<scope>test</scope>
   		</dependency>
   	</dependencies>
   </project>
   
   ```

3. 编写主代码

   在src/main/java/com/atguigu/maven目录下新建文件Hello.java

   ```java
   package com.atguigu.maven;
   
   public class Hello {
       public String sayHello(String name) {
           return "Hello"+name + "!";
       }
   }
   ```

4. 编写测试代码

   ```java
   package com.atguigu.maven;
   import org.junit.Test;
   import static junit.framework.Assert.*;
   
   public class HelloTest {
       public void testHello(String name) {
           Hello hello = new Hello();
           String results = hello.sayHello("caixiyu");
           assertEquals("Hello caixiyu",results);
       }
   }
   ```

5. 运行几个基本的Maven命令

   ```shell
   #打开终端，进入Hello项目根目录(pom.xml文件所在目录)：
   $ mvn compile  #查看根目录变化
   $ mvn clean    #再次查看根目录变化
   $ mvn  compile  #查看根目录变化
   $mvn  test-compile  #查看target目录的变化
   $ mvn  test  #查看target目录变化
   $ mvn  package  #查看target目录变化
   $ mvn  install  #查看本地仓库的目录变化
   ```

   **Maven 核心概念**

   1. 1. POM

         Project Object Model：项目对象模型。将Java工程的相关信息封装为对象作为便于操作和管理的模型。Maven工程的核心配置。可以说学习Maven就是学习pom.xml文件中的配置。

      2. 约定的目录结构

         现在JavaEE开发领域普遍认同一个观点：约定>配置>编码。意思就是能用配置解决的问题就不编码，能基于约定的就不进行配置。而Maven正是因为指定了特定文件保存的目录才能够对我们的Java工程进行自动化构建。目录结构含义参见前面的描述。

      3. 坐标

         - Maven的坐标

           > 使用如下三个向量在Maven的仓库中唯一的确定一个Maven工程。
           >
           > - ==g==roupId：公司或组织的域名倒序+当前项目名称
           >
           > - ==a==rtifactId：当前项目的模块名称
           >
           > - ==v==ersion：当前模块的版本
           >
           >   ```pom
           >   <groupId>com.atguigu.maven</groupId>
           >   <artifactId>Hello</artifactId>
           >   <version>0.0.1-SNAPSHOT</version>
           >   ```

         - 如何通过坐标到仓库中查找jar包？

         > 1. 将 gav三个向量连起来
         >
         >    ```
         >    com.atguigu.maven+Hello+0.0.1-SNAPSHOT
         >    ```
         >
         > 2. 以连起来的字符串作为目录结构到仓库中查找
         >
         >    ```
         >    com/atguigu/maven/Hello/0.0.1-SNAPSHOT/Hello-0.0.1-SNAPSHOT.jar
         >    ```

         ※注意：我们自己的Maven工程必须 `mvn install`才会进入仓库。

         

      4. **依赖**

         1. 

         - 当A jar包需要用到B jar包中的类时，我们就说A对B有依赖。配置的基本形式是使用dependency标签指定目标jar包的坐标。例如：

           ```pom
           <dependencies>
           		<dependency>
           			<groupId>junit</groupId>
           			<artifactId>junit</artifactId>
           			<scope>test</scope>
           </dependency>
           ```

         - 直接依赖和间接依赖

         如果A依赖B，B依赖C，那么A→B和B→C都是直接依赖，而A→C是间接依赖。

         1. 

         **依赖的范围**

         - compile

           > - main目录下的Java代码**可以**访问这个范围的依赖
           >
           > - test目录下的Java代码**可以**访问这个范围的依赖
           >
           > - 部署到Tomcat服务器上运行时**要**放在WEB-INF的lib目录下
           >
           >   例如：对Hello的依赖。主程序、测试程序和服务器运行时都需要用到

         

         - test

           > - main目录下的Java代码**不能**访问这个范围的依赖
           > - test目录下的Java代码**可以**访问这个范围的依赖
           > - 部署到Tomcat服务器上运行时**不会**放在WEB-INF的lib目录下
           >
           > 例如：对junit的依赖。仅仅是测试程序部分需要。

         - provided

           > - main目录下的Java代码**可以**访问这个范围的依赖
           > - test目录下的Java代码**可以**访问这个范围的依赖
           > - 部署到Tomcat服务器上运行时**不会**放在WEB-INF的lib目录下
           >
           > 例如：servlet-api在服务器上运行时，Servlet容器会提供相关API，所以部署的时候不需要。

         - 其它

           > runtime、import、system等。各个依赖范围的作用可以概括为下图：
           >
           > ![image-20200327190913887](pic/image-20200327190913887.png)

         

         **依赖的传递性**

         当存在间接依赖的情况时，主工程对间接依赖的jar可以访问吗？这要看间接依赖的jar包引入时的依赖范围——只有依赖范围为compile时可以访问。

         

         **依赖的原则：解决jar包冲突**

         1. 路径最短者优先

            ![image-20200327191105439](pic/image-20200327191105439.png)

         2. 路径相同时先声明者优先

         ​			![image-20200327191201357](pic/image-20200327191201357.png)

         这里“声明”的先后顺序指的是dependency标签配置的先后顺序。

         

         **依赖的排除**

         1. 有的时候为了确保程序正确可以将有可能重复的间接依赖排除。请看如下的例子：

         假设当前工程为public，直接依赖environment。environment依赖commons-logging的1.1.1对于public来说是间接依赖。当前工程public直接依赖commons-logging的1.1.2 

         加入exclusions配置后可以在依赖environment的时候排除版本为1.1.1的commons-logging的间 接依赖

         1. ```pom
            <dependency>
            	<groupId>com.atguigu.maven</groupId>
            	<artifactId>Environment</artifactId>
            	<version>0.0.1-SNAPSHOT</version>
            	<!-- 依赖排除 -->
            	<exclusions>
            		<exclusion>
            			<groupId>commons-logging</groupId>
            			<artifactId>commons-logging</artifactId>
            		</exclusion>
            	</exclusions>
            </dependency>
            <dependency>
            	<groupId>commons-logging</groupId>
            	<artifactId>commons-logging</artifactId>
            	<version>1.1.2</version>
            </dependency>
            ```

         2. 

         **统一管理目标jar包的版本**

         以对Spring的jar包依赖为例：Spring的每一个版本中都包含spring-core、spring-context等jar包。我们应该导入版本一致的Spring jar包，而不是使用4.0.0的spring-core的同时使用4.1.1的spring-context。

         问题是如果我们想要将这些jar包的版本统一升级为4.1.1，是不是要手动一个个修改呢？显然，我们有统一配置的方式

         

         

      5. 仓库

         - 分类

         > 本地仓库：为当前本机电脑上的所有Maven工程服务。
         >
         > 远程仓库
         >
         > ![maven仓库](pic/maven仓库.png)
         >
         > > 1.  私服：架设在当前局域网环境下，为当前局域网范围内的所有Maven工程服务。
         > > 2.  中央仓库：架设在Internet上，为全世界所有Maven工程服务。
         > > 3.  中央仓库的镜像：架设在各个大洲，为中央仓库分担流量。减轻中央仓库的压力，同时更快的响应用户请求。

         - 仓库中的文件

           1. Maven的插件
           2. 我们自己开发的项目的模块
           3. 第三方框架或工具的jar包

           ​	※不管是什么样的jar包，在仓库中都是按照坐标生成目录结构，所以可以通过统一的方式查询或依赖。

           

      6. 生命周期

         ​	Maven生命周期定义了各个构建环节的执行顺序，有了这个清单，Maven就可以自动化的执行构	建命令了。

         

         Maven有三套相互独立的生命周期，分别是：

         > - Clean Lifecycle在进行真正的构建之前进行一些清理工作。
         > - Default Lifecycle构建的核心部分，编译，测试，打包，安装，部署等等。
         > - Site Lifecycle生成项目报告，站点，发布站点。

         再次强调一下它们是**相互独立的**，你可以仅仅调用clean来清理工作目录，仅仅调用site来生成站点。当然你也可以直接运行 **mvn clean install site** 运行所有这三套生命周期。

         

         每套生命周期都由一组阶段(Phase)组成，我们平时在命令行输入的命令总会对应于一个特定的阶段。比如，运行mvn clean，这个clean是Clean生命周期的一个阶段。有Clean生命周期，也有clean阶段。

         1. 

         **clean生命周期**

         Clean生命周期一共包含了三个阶段：

         > - pre-clean 执行一些需要在clean之前完成的工作
         >
         > - clean 移除所有上一次构建生成的文件
         > - post-clean 执行一些需要在clean之后立刻完成的工作

         

         **Site生命周期**

         > - pre-site 执行一些需要在生成站点文档之前完成的工作
         > - site 生成项目的站点文档
         > - post-site 执行一些需要在生成站点文档之后完成的工作，并且为部署做准备
         > - site-deploy 将生成的站点文档部署到特定的服务器上

         1. 这里经常用到的是site阶段和site-deploy阶段，用以生成和发布Maven站点，这可是Maven相当强大的功能，Manager比较喜欢，文档及统计数据自动生成，很好看。

         

         **Default生命周期**

         Default生命周期是Maven生命周期中最重要的一个，绝大部分工作都发生在这个生命周期中。这里，只解释一些比较重要和常用的阶段：

         > - validate
         > - generate-sources
         > - process-sources
         > - generate-resources
         > - process-resources 复制并处理资源文件，至目标目录，准备打包。
         > - **compile** 编译项目的源代码。
         > - process-classes
         > - generate-test-sources
         > - process-test-sources
         > - generate-test-resources
         > - process-test-resources 复制并处理资源文件，至目标测试目录。
         > - **test-compile** 编译测试源代码。
         > - process-test-classes
         > - **test** 使用合适的单元测试框架运行测试。这些测试代码不会被打包或部署。
         > - prepare-package
         > - **package** 接受编译好的代码，打包成可发布的格式，如JAR。
         > - pre-integration-test
         > - integration-test
         > - post-integration-test
         > - verify
         > - **install**将包安装至本地仓库，以让其它项目依赖。
         > - deploy将最终的包复制到远程的仓库，以让其它开发人员与项目共享或部署到服务器上运行。

         

         **生命周期与自动化构建**

         **运行任何一个阶段的时候，它前面的所有阶段都会被运行**，例如我们运行mvn install 的时候，代码会被编译，测试，打包。这就是Maven为什么能够自动执行构建过程的各个环节的原因。此外，Maven的插件机制是完全依赖Maven的生命周期的，因此理解生命周期至关重要。

      7. 插件和目标

         - Maven的核心仅仅定义了抽象的生命周期，具体的任务都是交由插件完成的。
         - 每个插件都能实现多个功能，每个功能就是一个插件目标。
         - Maven的生命周期与插件目标相互绑定，以完成某个具体的构建任务。

         例如：compile就是插件maven-compiler-plugin的一个功能；pre-clean是插件maven-clean-plugin的一个目标。

         

      8. 继承

         由于非compile范围的依赖信息是不能在“依赖链”中传递的，所以有需要的工程只能单独配置。此时如果项目需要将各个模块的junit版本统一为4.9，那么到各个工程中手动修改无疑是非常不可取的。使用继承机制就可以将这样的依赖信息统一提取到父工程模块中进行统一管理。

         **创建父工程**

         创建父工程和创建一般的Java工程操作一致，唯一需要注意的是：打包方式处要设置为pom。

         在子工程中引用父工程

         在父工程中管理依赖

      9. 聚合

         将多个工程拆分为模块后，需要手动逐个安装到仓库后依赖才能够生效。修改源码后也需要逐个手动进行clean操作。而使用了聚合之后就可以批量进行Maven工程的安装、清理工作。

         在总的聚合工程中使用modules/module标签组合，指定模块工程的相对路径即可

         ```
         <modules>
         	<module>../Hello</module>
         	<module>../HelloFriend</module>
         	<module>../MakeFriends</module>
         </modules>
         ```

         

6. 

#### 第二个Maven工程

关键：对Hello的依赖

这里Hello就是我们的第一个Maven工程，现在HelloFriend对它有依赖。那么这个依赖能否成功呢？更进一步的问题是：HelloFriend工程会到哪里去找Hello呢？

答案是：本地仓库。任何一个Maven工程会根据坐标到本地仓库中去查找它所依赖的jar包。如果能够找到则可以正常工作，否则就不行。



#  Spring

### 概述

1. Spring是一个开源框架 	

2. Spring为==简化==企业级开发而生，使用Spring，JavaBean就可以实现很多以前要靠EJB(Enterprise Java Beans)才能实现的功能。同样的功能，在EJB中要通过繁琐的配置和复杂的代码才能够实现，而在Spring中却非常的优雅和简洁。 	

3. Spring是一个**IOC**(DI)和**AOP**容器框架。

4. Spring的优良特性

   > **依赖注入**：DI——Dependency Injection，反转控制(IOC)最经典的实现。
   >
   > **面向切面编程**：Aspect Oriented Programming——AOP
   >
   > **一站式**：在IOC和AOP的基础上可以整合各种企业应用的开源框架和优秀的第三方    类库（实际上Spring 自身也提供了表述层的SpringMVC和持久层的Spring JDBC）。

5. Spring模块

   ![image-20200327231815063](pic/image-20200327231815063.png)

6.  什么是==IOC容器==

    - IOC不是一种技术，只是一种思想，一个重要的面向对象编程的法则，它能指导我们如何设计出松耦合，更优良的程序。传统应用程序都是由我们在类内部主动创建依赖对象，从而导致类与类之间高耦合，难于测试；

    - 有了IOC容器后，把==创建和查找依赖对象的控制权交给了容器==，由容器进行注入组合对象，所以对象与对象之间是松散耦合，这样也方便测试，==利于功能复用==，更重要的使程序的整个体系结构变得非常灵活。在运行期，在外部容器动态的将依赖对象注入组件，当外部容器启动后，外部容器就会初始化。创建并管理bean对象，以及销毁他，这种应用本身不负责依赖对象的创建和维护，依赖对象的创建和维护是由外部容器负责的称为控制反转。

    - 2.IOC（控制反转）和 DI（依赖注入）

      ==IOC（Inversion of Control==，控制反转）。这是spring的核心，贯穿始终。所谓IOC，对于spring框架来说，就是由spring来负责控制对象的生命周期和对象间的关系。

    - DI（依赖注入）。IOC的一个重点是在系统运行中，动态的向某个对象提供它所需要的其他对象。这一点是通过DI（Dependency Injection，依赖注入）来实现的





### 搭建Spring环境

#### 1.创建Maven版的Java工程

此处不用选archetype,直接next ,创建springMVC的时候才选勾上,然后选web项目

![img](pic/1068501-20180914191722384-1695467171.png)

![img](pic/1068501-20180914191929721-1110836003.png)



<img src="pic/20180104102227025" alt="img" style="zoom:120%;" />

<img src="pic/20180104102149285" alt="img" style="zoom:120%;" />

<img src="pic/20180104102307530" alt="img" style="zoom:120%;" />



**注: Eclipse中, 在Springboot之前,packaging都是选war包**

#### 2. 在pom.xml 中加入Spring相关jar包的依赖Tips: Spring自身JAR包：

> spring-beans-4.0.0.RELEASE.jar
>
> spring-context-4.0.0.RELEASE.jar
>
> spring-core-4.0.0.RELEASE.jar
>
> spring-expression-4.0.0.RELEASE.jar
>
> commons-logging-1.1.1.jar



在加入依赖时，==**实际**只需要加入对 spring-context的依赖==即可,Maven会根据依赖信息，将其他的jar包的依赖一并导入

```xml
 <dependencies>
        <!-- beans  -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-beans</artifactId>
            <version>4.0.0.RELEASE</version>
        </dependency>

        <!-- context -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>4.0.0.RELEASE</version>
        </dependency>

        <!-- core -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
            <version>4.0.0.RELEASE</version>
        </dependency>

        <!-- expression -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-expression</artifactId>
            <version>4.0.0.RELEASE</version>
        </dependency>

 </dependencies>
```

下载依赖包的过程可能比较慢，可从本地导入，但不建议：

```shell
mvn install:install-file -Dfile=spring-context-4.0.0.RELEASE.jar  -DgroupId=org.springframework -DartifactId=spring-context  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile=spring-beans-4.0.0.RELEASE.jar  -DgroupId=org.springframework -DartifactId=spring-beans  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile=spring-core-4.0.0.RELEASE.jar -DgroupId=org.springframework -DartifactId=spring-core  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile=spring-expression-4.0.0.RELEASE.jar -DgroupId=org.springframework -DartifactId=spring-expression  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile= commons-logging-1.1.1.jar -DgroupId=org.springframework -DartifactId= commons-logging  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile=spring-context-support-4.0.0.RELEASE.jar -DgroupId=org.springframework -DartifactId= spring-context-support  -Dversion=4.0.0 -Dpackaging=jar
spring-context-support-4.0.0.RELEASE.jar
```

#### 3.在Spring Tool Suite工具中通过如下步骤创建Spring的配置文件

> - src/main/resources 下：New XML file->Spring Bean Configuration File
>
> - 为文件取名字 例如：applicationContext.xml
>
>   ```xml
>   <?xml version="1.0" encoding="UTF-8"?>
>   <beans xmlns="http://www.springframework.org/schema/beans"
>          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
>          xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
>   
>       <!-- 配置bean
>           id属性：配置bean的名称，该属性值在IOC容器中是唯一的，自动设置为类名的首字母小写
>           class属性：配置bean的全类名，Spring会利用反射技术实例化该bean
>       -->
>       <bean id="helloWorld" class="com.atguigu.spring.helloworld.HelloWorld">
>           <!-- 通过property标签给bean的属性赋值,会调用set方法给各个属性赋值 -->
>           <property name="name" value="Spring"></property>
>       </bean>
>   </beans>
>   ```

#### 4. 写一个类HelloWorld，在类中写set方法

​	

### HelloWorld

1. 目标：使用Spring创建对象，为属性赋值

2. 创建HelloWorld类

   ```java
   public class HelloWorld {
       private String name;
   
       public HelloWorld() {
           System.out.println("HelloWorld对象被创建了");
       }
   
       public void setName(String name) {
           System.out.println("setName方法被调用了");
           this.name = name;
       }
   
       public void sayHello(){
           System.out.println("Hello ," + name);
       }
   }
   ```

3. 测试

   ```java
   public class HelloWorldTest {
       @Test
       void test(){
           //创建IOC容器对象
           ApplicationContext ioc = new ClassPathXmlApplicationContext("applicationContext.xml");
   
           //从IOC容器中获取HelloWorld对象
           HelloWorld helloWold = (HelloWorld) ioc.getBean("helloWorld");
   
           //调用sayHello方法
           helloWold.sayHello();
       }
   }
   ```

   

4. 报错解决：

> - 版本号5已过时：将Settings中的Java compiler中的 Target codebite version 在Project structure中改为 和当前工程下当前Project下的Java version ， current language level 以及 Module 中的 language level同步
> - 一直不能更新dependency，看看是不是没有更改maven的仓库的位置

### Spring Bean 的配置

#### IOC 和 DI 简介

##### IOC(Inversion of Control)：反转控制

在应用程序中的组件需要获取资源时，传统的方式是组件==主动==的从容器中获取所需要的资源，在这样的模式下开发人员往往需要知道在具体容器中特定资源的获取方式，增加了学习成本，同时降低了开发效率。

反转控制的思想完全颠覆了应用程序组件获取资源的传统方式：==反转了资源的获取方向==——改由容器主动的将资源推送给需要的组件，开发人员不需要知道容器是如何创建资源对象的，只需要提供接收资源的方式即可，极大的降低了学习成本，提高了开发的效率。这种行为也称为查找的==被动形式==。



#####  DI(Dependency Injection)：依赖注入

IOC的另一种表述方式：即**组件以一些预先定义好的方式(例如：setter 方法)接受来自于容器的资源注入**。相对于IOC而言，这种表述更直接。

IOC 描述的是一种思想，而DI 是对IOC思想的具体实现.

#### Bean配置解释

```xml
<bean>: 让IOC容器管理一个具体的对象.
				id:  唯一标识
    		class: 类的全类名. 通过反射的方式创建对象. 
			  Class cls = Class.forName("com.atguigu.spring.helloWorld.Person");
				Object obj  = cls.newInstance(); 无参数构造器
			<property>: 给对象的属性赋值.
				name: 指定属性名 ，要去对应类中的set方法. 
				value:指定属性值	
```



#### 获取Bean的方式

1. 从IOC容器中获取bean时，除了通过id值获取，还可以通过bean的类型获取。但如果同一个类型的bean在XML文件中配置了多个，则获取时会抛出异常，所以==同一个类==的bean在容器中必须是==唯一==的。

   ```java
   HelloWorld helloWold = (HelloWorld) ioc.getBean("helloWorld");
   ```

2. 或者可以使用另外一个重载的方法，id值。也可以同时指定id和类，但不建议

   ```java
   HelloWorld helloWorld2 = ioc.getBean(HelloWorld.class);
   ```

#### 给bean的属性赋值

1. 普通类型的 value 或者使用<value>子标签

2. 引用类型的值

   如果Employee类中定义了Department类型的成员变量.

```xml
<bean id="employee" class="com.atguigu.spring.beans.Employee">
        <property name="id" value="100"></property>
        <property name="lastName" value="zaitianlin"></property>
        <property name="email" value="ztl@163.com"></property>
        <property name="dept" ref="department"></property>
        <!-- 通过级联属性修改属性值-->
        <property name="dept.id" value="1002"></property>
    </bean>

    <bean id="department" class="com.atguigu.spring.beans.Department">
        <property name="id" value="1001"></property>
        <property name="name" value="造假部"></property>
    </bean>
```

#### 引用外部属性文件

​	当bean的配置信息逐渐增多时，查找和修改一些bean的配置信息就变得愈加困难。这时可以将一部分信息提取到bean配置文件的外部，以properties格式的属性文件保存起来，同时在bean的配置文件中引用properties属性文件中的内容，从而实现一部分属性值在发生变化时仅修改properties属性文件即可。这种技术多用于连接数据库的基本信息的配置。

##### 直接配置

```xml
<!--直接配置数据源-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="username" value="root"></property>
        <property name="password" value="12345c"></property>
        <property name="url" value="jdbc:mysql://localhost:3306/test"></property>
        <property name="driverClassName" value="com.mysql.jdbc.Driver"></property>
    </bean>
```

#####使用外部的属性文件

1. 创建properties属性文件

```properties
jdbc.username=root
jdbc.password=root
jdbc.url=jdbc:mysql://localhost:3306/test
jdbc.driverClassName=com.mysql.jdbc.Driver
jdbc.initialSize=10
jdbc.minIdle=5
jdbc.maxActive=20
jdbc.maxWait=5000
```

2. 引入context命名空间

​	![img](pic/20180919164127668.gif)

在编辑区，直接输入想要配置的标签，然后输入冒号(：)，自动提示了可能需要配置的标签以及对应的命名空间。选择我们对应的标签，命名空间自动就导入了

3. 指定properties属性文件的位置

```xml
    <context:property-placeholder location="druid.properties"/>
```

 4.从properties属性

```xml
    <context:property-placeholder location="druid.properties"/>
    <!--从properties属性文件中引入属性值 -->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="username" value="${jdbc.username}"/>
        <property name="password" value="${jdbc.password}"/>
        <property name="url" value="${jdbc.url}"/>
        <property name="driverClassName" value="${jdbc.driverClassName}"/>
        <property name="initialSize" value="${jdbc.initialSize}"/>
        <property name="minIdle" value="${jdbc.minIdle}"/>
        <property name="maxActive" value="${jdbc.maxActive}"/>
        <property name="maxWait" value="${jdbc.maxWait}"/>
    </bean>
```

### 基于注解配置bean

#### 1. 自动装配

##### 自动装配的概念

1. 手动装配：以value或ref的方式**明确指定属性值**都是手动装配。
2. 自动装配：根据指定的装配规则，**不需要明确指定**，Spring**自动**将匹配的属性值**注入**bean中。

##### 装配模式

1. 根据**类型**自动装配：将类型匹配的bean作为属性注入到另一个bean中。若IOC容器中有多个与目标bean类型一致的bean，Spring将无法判定哪个bean最合适该属性，所以不能执行自动装配
2. 根据**名称**自动装配：必须将目标bean的名称和属性名设置的完全相同
3. 通过构造器自动装配：当bean中存在多个构造器时，此种自动装配方式将会很复杂。不推荐使用。

##### 选用建议

​	相对于使用注解的方式实现的自动装配，在XML文档中进行的自动装配略显笨拙，在项目中更多的使用==注解==的方式实现。



#### 2. 通过注解配置bean

#####概述

​	相对于XML方式而言，通过注解的方式配置bean更加简洁和优雅，而且和MVC组件化开发的理念十分契合，是开发中常用的使用方式。



##### 使用注解标识组件

1. 普通组件：@Componen：标识一个受Spring IOC容器管理的组件
2. 持久化层组件：@Repository：标识一个受Spring IOC容器管理的持久化层组件
3. 业务逻辑层组件：@Service：标识一个受Spring IOC容器管理的业务逻辑层组件
4. 表述层控制器组件：@Controller：标识一个受Spring IOC容器管理的表述层控制器组件
5. 组件命名规则

​	①默认情况：使用组件的简单类名==首字母小写==后得到的字符串作为bean的id

​	②使用组件注解的value属性指定bean的id

​	注意：事实上Spring并没有能力识别一个组件到底是不是它所标记的类型，即使将@Respository注解用在一个表述层控制器组件上面也不会产生任何错误，所以			@Respository、@Service、@Controller这几个注解仅仅是为了让开发人员自己明确当前的组件扮演的角色。

#####扫描组件

​	组件被上述注解标识后还需要通过Spring进行扫描才能够侦测到。

1. 指定被扫描的package

```xml
<context:component-scan base-package="com.atguigu.spring.annotation"></context:component-scan>
```

1. 详细说明:

- **base-package**属性指定一个需要扫描的基类包，Spring容器将会扫描这个基类包及其子包中的所有类。
- 当需要扫描多个包时可以使用逗号分隔。
- 如果仅希望扫描特定的类而非基包下的所有类，可使用==resource-pattern==属性过滤特定的类，示例：

```xml
<context:component-scan base-package="com.atguigu.spring.annotation" resource-pattern="dao/*.class"/>
```

- 包含与排除

  > `<context:include-filter>` 子节点表示要==包含==的目标类
  >
  > > 注意：通常需要与==use-default-filters==属性配合使用才能够达到“仅包含某些			组件”这样的效果。即：通过将use-default-filters属性设置为false，			禁用默认过滤器，然后扫描的就只是include-filter中的规则指定组件了
  >
  > `<context:exclude-filter>` 子节点表示要==排除在外==的目标类

​		

component-scan下可以拥有若干个include-filter和exclude-filter子节点

```xml
<!--    <context:component-scan base-package="com.atguigu.spring.annotation"></context:component-scan>-->
<!--    &lt;!&ndash;不扫描dao包下的类&ndash;&gt;-->
<!--    <context:component-scan base-package="com.atguigu.spring.annotation" resource-pattern="dao/*.class"/>-->

<!--    <context:component-scan base-package="com.atguigu.spring.annotation" use-default-filters="false">-->
<!--            &lt;!&ndash;-->
<!--            子标签context:include-filter :用来设置扫描哪个包下的类-->
<!--            注意：此时需要将父标签的use-default-filters="false"-->
<!--                    如果type="annotation"，则expression对应的是注解的全类名-->
<!--                    如果type="assignable"，则expression对应的是接口或实现类的全类名-->
<!--            &ndash;&gt;-->
<!--&lt;!&ndash;            <context:include-filter type="annotation" expression="org.springframework.stereotype.Repository"/>&ndash;&gt;-->
<!--            <context:include-filter type="assignable" expression="com.atguigu.spring.annotation.dao.UserDao"/>-->
<!--        </context:component-scan>-->

    <context:component-scan base-package="com.atguigu.spring.annotation" use-default-filters="false">
        <!--
        子标签context:include-filter :用来设置不扫描哪个包下的类
        注意：此时需要将父标签的use-default-filters="false"
                如果type="annotation"，则expression对应的是注解的全类名
                如果type="assignable"，则expression对应的是接口或实现类的全类名
        -->
                    <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Repository"/>
        <context:exclude-filter type="assignable" expression="com.atguigu.spring.annotation.dao.UserDao"/>
    </context:component-scan>
```

#####组件装配

2. **需求**

​	Controller组件中往往需要用到Service组件的实例，Service组件中往往需要用到	Repository组件的实例。Spring可以通过注解的方式帮我们实现属性的装配。

2. **实现依据**[了解]

​	在指定要扫描的包时，<context:component-scan> 元素会自动注册一个bean的后置处理器：AutowiredAnnotationBeanPostProcessor的实例。该后置处理器可以 自动装配标记了**@Autowired**、**@Resource**或 **@Inject**注解的属性。

3. **@Autowired注解**

> ①根据类型实现自动装配。
>
> ②构造器、普通字段(即使是非public)、一切具有参数的方法都可以应用@Autowired注解
>
> ③默认情况下，所有使用@Autowired注解的属性都需要被设置。当Spring找不到匹		  配的bean装配属性时，会抛出异常。
>
> ④若某一属性允许不被设置，可以设置==@Autowired注解的required属性为 false==
>
> ⑤默认情况下，当IOC容器里存在多个类型兼容的bean时，Spring会尝试匹配bean的id值是否与变量名相同，
>
> > 如果相同则进行装配。
> >
> > 如果bean的id值不相同，通过类型的自动装配将无法工作。此时可以在@Qualifier注解里提供bean的名称。Spring甚至允许在方法的形参上标注@Qualifiter注解以指定注入bean的名称。
>
> ⑥@Autowired注解也可以应用在数组类型的属性上，此时Spring将会把所有匹配的bean进行自动装配。
>
> ⑦@Autowired注解也可以应用在集合属性上，此时Spring读取该集合的类型信息，然后自动装配所有与之兼容的bean。
>
> ⑧@Autowired注解用在java.util.Map上时，若该Map的键值为String，那么 Spring将自动装配与值类型兼容的bean作为值，并以bean的id值作为键。

​		

4. ###### @Resource

​	@Resource注解要求提供一个bean名称的属性，若该属性为空，则自动采用标注处的变量或方法名作为bean的名称。

5.**@Inject**

​	@Inject和@Autowired注解一样也是按类型注入匹配的bean，但没有reqired属性。

# Spring Web MVC (SpringMVC)

### 1. SpringMVC 概述

1. 一种轻量级的、基于MVC的Web层应用框架。偏前端而不是基于业务逻辑层。Spring框架的一个后续产品。 	
2. Spring 为展现层提供的基于 MVC 设计理念的优秀的 Web 框架，是目前最主流的MVC 框架之一
3. Spring MVC 通过一套 MVC 注解，让 POJO 成为处理请求的控制器，而无须实现任何接口

### 2. SpringMVC HelloWorld

1. [创建Maven版的Web工程](#1.创建Maven版的Java工程)

2. 在讲Spring时导入 的jar包依赖的基础上，加入对web相关jar包的依赖

   ```xml
    <!-- context -->
   <dependency>
         <groupId>org.springframework</groupId>
         <artifactId>spring-context</artifactId>
         <version>4.0.0.RELEASE</version>
   </dependency>
       
   <!--webmvc-->
   <dependency>
             <groupId>org.springframework</groupId>
             <artifactId>spring-webmvc</artifactId>
             <version>4.0.0.RELEASE</version>
   </dependency>
   ```

   Tips: 实际需要加入spring-web与spring-webmvc的jar包，因为spring-webmvc 依赖

   ​		  了spring-web, Maven会自动维护此依赖，因此只需加入对spring-webmvc的依   

   ​          赖.

3. 在==web.xml==中配置DispatcherServlet

   ```xml
   <!-- 前端控制器/核心控制器 :DispatcherServlet -->
   	<servlet>
   		<servlet-name>springDispatcherServlet</servlet-name>
   		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
   		<init-param>
   			<param-name>contextConfigLocation</param-name>
   			<param-value>classpath:springmvc.xml</param-value>
   		</init-param>
   		<load-on-startup>1</load-on-startup>
   	</servlet>
   
   <!--配置映射请求地址-->
   	<servlet-mapping>
   		<servlet-name>springDispatcherServlet</servlet-name>
   		<url-pattern>/</url-pattern>
   	</servlet-mapping>
   ```

   

4. 加入SpringMVC的配置文件 ==springmvc.xml==

   - 添加命名空间

   - 配置组件扫描 和视图解析器

     ```xml
     <!-- 组件扫描 -->
     <context:component-scan base-package="com.atguigu.springmvc"></context:component-scan>
     
     <!-- 视图解析器 -->
     <bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
             <property name="prefix" value="/WEB-INF/views/"></property>
             <property name="suffix" value=".jsp"></property>
     </bean>
     ```

5. 创建一个入口页面，index.jsp

   在页面中编写超链接:

   `<a href="${pageContext.request.contextPath }/hello">Hello Springmvc </a>` 

6. 编写请求处理器

   ```java
   /**
    * 请求处理器
    */
   @Controller
   public class HelloWorldHandler {
   	/**
   	 * 请求处理方法
   	 * 浏览器端: http://localhost:8080/Springmvc01/hello
        * 方法的返回值会被SpringMVC配置文件中的InternalResourceViewResolver这个试图解析器解析为真实的物理地址
        * 然后自动进行请求的转发
        * 真实的物理视图 = 前缀 + 方法返回值 + 后缀
        * 即: /WEB-INF/views/success.jsp
        * @return
        */
   	@RequestMapping(value="/hello")
   	public  String   handleHello() {
   		System.out.println("Hello Springmvc .");
   		return "success";   
   	}	
   }
   ```

7. 编写视图页面

   在/WEB-INF/views下新建success.jsp页面

8. 部署测试

   注: 如果浏览器跳转的页面乱码,可能是web.xml版本问题,解决如下:

   问题描述：用idea的maven新建一个webapp项目，自动生成的web.xml默认版本是2.3版本（这版本连EL表达式都默认不能使用，无语了）。

   Servlet 2.3：

   [![复制代码](pic/copycode.gif)](javascript:void(0);)

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE web-app
       PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
       "http://java.sun.com/dtd/web-app_2_3.dtd">
   <web-app>
   </web-app>
   ```

   [![复制代码](pic/copycode-1586334239881.gif)](javascript:void(0);)

   1. **临时解决办法：**

   把web.xml删掉。在Project Structure 里面的Modules重新添加一个Web.xml，能够生成并选择版本，但是这只是作用于当前项目。 

   

   **2. 永久解决办法：**

   修改默认版本，具体步骤如下：

    

   ![img](pic/1745551-20190725191758788-1324700232.png)

    

   ![img](pic/1745551-20190725191846707-1566801207.png)

    

    进入“1.3”文件夹，找到jar包，如下图

    

   ![img](pic/1745551-20190725191943931-1726254123.png)

    

   用解压软件打开文件,记住不是解压

    

   ![img](pic/1745551-20190725192135089-1717773106.png)

    

   按下图这个路径依次打开，找到web.xml文件：

   

   ![img](pic/1745551-20190725192211852-17025032.png)

    

   直接打开web.xml，修改头文件，保存就可以了(注意：是在解压软件打开的的界面直接打开并修改web.xml，而不是解压成文件夹之后修改，也就是要保证jar包本来的结构不变)。

   下面这个就是3.0的web.xml头文件，直接复制就可以。

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 　　　　　xmlns="http://java.sun.com/xml/ns/javaee" 　　　　  xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd" id="WebApp_ID" version="3.0">
   ```

    

   原因：用maven新建webapp项目时，就是以这个***1.3.jar包里的web.xml为模板去生成新项目的web.xml，所以修改它就等于修改了模板。

   

   如果转发找不到页面,但路径正确 . ==看是不是自己没有导入spring-context依赖==.

   

9. 流程解析

   ![image-20200403144458952](pic/image-20200403144458952.png)



### 3. @RequestMapping 映射请求注解

#### 1. @RequestMapping 概念

- 1. SpringMVC使用@RequestMapping注解为控制器==指定可以处理哪些URL请求==
  2. 作用：DispatcherServlet 截获请求后，就通过控制器上@RequestMapping 提供的映射信息确定请求所对应的处理方法。 			

#### 2. @RequestMapping 可标注的位置

```java
真实的物理视图 = 前缀 + 方法返回值 + 后缀
即: /WEB-INF/views/success.jsp
 
URL = 当前项目地址 + 类的 @RequestMapping 的value + 方法的 @RequestMapping 的value
```

@RequestMapping 可标注的位置: 方法或类 . 如果类没有 @RequestMapping ,则默认为 /



#### 3. @RequestMapping 映射请求URL与 请求方式

##### @RequestMapping 注解中的属性:

1. value属性

   用来设置要==请求的地址==(即在浏览器地址栏的请求地址), 值的类型是String类型的数组. 如果映射多个请求地址,需要加大括号{}. value属性名可以不写

2. method属性

   用来设置要映射的请求方式. 如果没有设置该属性,则不管请求方式,只看请求地址对不对



### 4. 处理请求数据

#### 1 请求处理方法签名

1. Spring MVC 通过分析处理方法的签名，将HTTP请求信息绑定到处理方法的相应入参中。
2. Spring MVC 对控制器处理方法签名的限制是很宽松的，几乎可以按喜欢的任何方式对方法进行签名。

#### 2 @RequestParam注解

- 用来映射请求参数

  如果Handler的方法的==入参==(注入参数)中的参数名与请求参数名一致,那么该注解可以省略不写(不建议)

- 该注解的属性

  > 1）在处理方法入参处使用@RequestParam可以把==请求参数传递给请求方法==
  >
  > 2）value：参数名
  >
  > 3）required：是否必须。==默认为 true==, 表示请求参数中必须包含对应的参数，若不存在，将抛出异常
  >
  > 4）defaultValue: 默认值，当没有传递参数时使用该值



#### 3 使用POJO作为参数

传参数可能要传的参数很多, 能传对象的话会简单很多

1. 使用 ==POJO (Plain Old/Ordinary Java Object)==对象绑定请求参数值
2. Spring MVC **会按请求参数名和** **POJO** **属性名进行自动匹配，自动为该对象填充属性值**。**支持级联属性**。如：dept.deptId、dept.address.tel 等
3. 解决jsp页面中文乱码:<%@page contentType="text/html;charset=utf-8"%>

#### 4 使用Servlet原生API作为参数

1. MVC 的 Handler 方法可以接受哪些 ServletAPI 类型的参数

> 1. ★HttpServletRequest
>
> 2. ★HttpServletResponse
>
> 3. ★HttpSession
>
> 4. java.security.Principal
>
> 5. Locale
>
> 6. InputStream
>
> 7. OutputStream
>
> 8. Reader
>
> 9. Write

###  5. 处理响应数据

#### 1 SpringMVC 处理响应数据概述

1. **ModelAndView**: 处理方法返回值类型为 ModelAndView 时, 方法体即可通过该对象添加模型数据  

2. **Map** **及** **Model**:入参为 

   org.springframework.ui.Model, 

   org.springframework.ui.ModelMap 

   或 java.uti.Map 时，

   处理方法返回时，Map 中的数据会自动添加到模型中。

#### 2 处理响应数据之 ModelAndView

1. 控制器处理方法的返回值如果为 ModelAndView, 则其既包含视图信息，也包含模型

数据信息。

2. 添加模型数据:

```java
MoelAndView addObject(String attributeName, Object attributeValue)

ModelAndView addAllObject(Map<String, ?> modelMap)
```

3. 设置视图:

```java
void setView(View view)

void setViewName(String viewName)
```

```java
    /**
     *处理数据响应方式一: 将Handler的方法返回值设置为ModelAndView
     */
    @RequestMapping("/testModelAndView")
    public ModelAndView testModelAndView(){
        //创建ModelAndView对象
        ModelAndView mv = new ModelAndView();
        //假设从数据库中查询出一个Employee对象
        Employee employee = new Employee(1,"张三丰","zsf@qq.com",null);
        //将模型数据设置到ModelAndView中
        mv.addObject("emp",employee);
        //设置视图名
        mv.setViewName("success");
        //返回ModelAndView对象
        return mv;
    }
```



#### 3 处理响应数据之 Map 、Model

- Spring MVC 在内部使用了一个 org.springframework.ui.Model 接口存储模型数据

- **Spring MVC** **在调用方法前会创建一个隐含的模型对象作为模型数据的存储容器**。

- 如果方法的入参为 **Map** **或** **Model** **类型**，Spring MVC 会将隐含模型的引用传递给这些入参。

- 在方法体内，开发者可以通过这个入参对象访问到模型中的所有数据，也可以向模型中添加**新的属性数据**

  ```java
      /**
       * ★处理数据响应方式二: 将Handler的方法中传入Map/Model/ModelMap
       * 不管将Handler的方法返回值设置为ModelAndView还是 将Handler的方法中传入Map/Model/ModelMap
       * SpringMVC都会转换为一个ModelAndView对象
       */
      @RequestMapping("/testMap")
      public String testMap(Map<String,Object> map){
          //假设从数据库中查询出一个Employee对象
          Employee employee = new Employee(1,"张无忌","zwj@zzr.com",null);
          //将employee对象放到map中,最后会放到request域中
          map.put("emp",employee);
          return "success";
      }
  ```

  

#### 4 @ResponseBody注解

​	在Handler方法上添加该注解之后，方法的返回值将以==字符串的形式==直接响应给浏览器,而不是和前缀后缀一起作为真实地址转发。

#### 5 重定向

2. 一般情况下，控制器方法返回字符串类型的值会被当成逻辑视图名处理

3. 如果返回的字符串中带 **forward:** **或** **redirect:** 前缀时，SpringMVC 会对他们进行特殊处理：将 forward: 和 redirect: 当成指示符，其后的字符串作为 URL 来处理

4. redirect:success.jsp：会完成一个到 success.jsp 的重定向的操作

5. forward:success.jsp：会完成一个到 success.jsp 的转发操作

#### 6. 处理静态资源[了解]

在springmvc的配置文件中加入如下两个配置:

```xml
<!--配置处理静态资源-->
<mvc:default-servlet-handler/>
<!--配置了处理静态资源后,Handler方法上的@RequestMaping注解将失效,此时必须重新配置以下标签:-->
<mvc:annotation-driven></mvc:annotation-driven>
```

1. 

###6. Spring 与 Springmvc的整合

#### 1 Spring 与SpringMVC的整合问题：

1. 需要进行 Spring 整合 SpringMVC 吗 ? 

   - 不整合

     > 将所有的配置都配置到SpringMVC配置文件中
     >
     > 将其他配置文件用过import标签导入SpringMVC文件中

   - 整合

     > Spring的IOC的容器负责配置Dao,Service,数据源,事务以及其他框架的整合
     >
     > SpringMVC负责配置Handler,视图解析器等

   问题一:

   > IOC容器如何初始化?
   >
   > > Java工程: new ClassPathApplicationCOntext(“beans.xml”)
   > >
   > > Web工程: 在web.xml中配置ContextLoaderListener监听器,需新建一个Spring的配置文件:bea

   问题二:

   > Handler和Service对象创建了2次
   >
   > 解决:
   >
   > > Spring(配置文件beans)不扫描Handler
   > >
   > > SpringMVC(配置文件springmvc)只扫描Handler

2. 还是否需要再加入 Spring 的 IOC 容器 ?  

3. 是否需要在web.xml 文件中配置启动 Spring IOC 容器的 ContextLoaderListener ?

   - 需要: 通常情况下, 类似于数据源, 事务, 整合其他框架都是放在 Spring 的配置文件中(而不是放在 SpringMVC 的配置文件中).实际上放入 Spring 配置文件对应的 IOC 容器中的还有 Service 和 Dao.
   - 不需要: 都放在 SpringMVC 的配置文件中. 也可以分多个 Spring 的配置文件, 然后使

​       用 import 节点导入其他的配置文件 

#### Spring整合SpringMVC_解决方案配置监听器

1. 监听器配置:web.xml

2. ```xml
   <!--配置监听器-->
   <context-param>
           <param-name>contextConfigLocation</param-name>
           <param-value>classpath:beans.xml</param-value>
   </context-param>
   <listener>
           <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
   </listener>
   ```

3. 创建Spring的bean的配置文件：beans.xml

4. ```xml
   <context:component-scan base-package="com.atguigu.ss">
   ```

5. springmvc配置文件：springmvc.xml

```xml
<!-- 设置自动扫描的包-->
<context:component-scan base-package="com.atguigu.ss" ></context:component-scan>
```

​	在HelloWorldHandler、UserService类中增加构造方法，启动服务器，查看构造器执行情况。

问题: 若 Spring 的 IOC 容器和 SpringMVC 的 IOC 容器扫描的包有重合的部分, 就会导致有的 bean 会被==创建 2 次==.

**解决****:**

使 Spring 的 IOC 容器扫描的包和 SpringMVC 的 IOC 容器扫描的包没有重合的部分.

使用 exclude-filter 和 include-filter 子节点来规定只能扫描的注解

​	**springmvc.xml** :

```xml
<!--这是Spring的配置文件-->
<context:component-scan base-package="com.atguigu.ss">
        <!--设置不扫描Handler-->
        <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
</context:component-scan>
```

**beans.xml** :

```xml
<!-- 设置自动扫描的包-->
<context:component-scan base-package="com.atguigu.ss" use-default-filters="false">
        <!--设置只扫描Handler-->
        <context:include-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
</context:component-scan>
```

####SpringIOC 容器和 SpringMVC IOC 容器的关系

SpringMVC 的 IOC 容器中的 bean 可以来引用 Spring IOC 容器中的 bean.

返回来呢 ? 反之则不行. Spring IOC 容器中的 bean 却不能来引用 SpringMVC IOC 容器中的 bean 

1. 

# SpringBoot

### 1 分布式架构

#### 1.1 流行分布式架构

![image-20200404170149951](pic/image-20200404170149951.png)

#### 1.2 Spring分布式架构

![image-20200404170226678](pic/image-20200404170226678.png)

### 2 SpringBoot起步

#### 2.1 概述

Spring Boot是由Pivotal团队提供的全新框架，其设计目的是用来简化新Spring应用的初始搭建以及开发过程。

该框架使用了特定的方式来进行配置，从而使开发人员不再需要定义样板化的配置。

通过这种方式，Spring Boot致力于在蓬勃发展的快速应用开发领域(rapid application development)成为领导者。

本章内容只是在web项目中应用基本的Spring Boot技术，如果想要学习完整Spring Boot课程内容，请访问Spring Boot官网进行学习。

此课件基于Maven创建项目，如果对于Maven工具不是很了解，请自行学习相关课件

#### 2.2 为什么使用Spring Boot？

说到为什么使用Spring Boot, 就不得不提到Spring框架的前世今生

Spring框架由于其繁琐的配置，一度被人认为“配置地狱”，各种XML、Annotation配置混合使用，让人眼花缭乱，而且如果出错了也很难找出原因。

通过SpringMVC框架部署和发布web程序，需要和系统外服务器进行关联，操作繁琐不方便。

Spring Boot是由Spring官方推出的一个新框架，对Spring进行了高度封装，是Spring未来的发展方向。使用Spring Boot框架后，可以帮助开发者快速搭建Spring框架，也可以帮助开发者快速启动一个Web服务，无须依赖外部Servlet容器，使编码变得简单，使配置变得简单，使部署变得简单，使监控变得简单。

#### 2.3 Spring前世今生

##### 2.3.1 Spring1.x 时代

在Spring1.x时代，都是通过xml文件配置bean

随着项目的不断扩大，需要将xml配置分放到不同的配置文件中

需要频繁的在java类和xml配置文件中切换。

##### 2.3.2 Spring2.x时代

随着JDK 1.5带来的注解支持，Spring2.x可以使用注解对Bean进行申明和注入，大大的减少了xml配置文件，同时也大大简化了项目的开发。 

那么，问题来了，究竟是应该使用xml还是注解呢？

​			最佳实践： 		应用的基本配置用xml，比如：数据源、资源文件等； 		 		 		业务开发用注解，比如：Service中注入bean等； 		 		 	

##### 2.3.3 Spring3.x到Spring4.x

从Spring3.x开始提供了Java配置方式，使用Java配置方式可以更好的理解你配置的Bean，

现在我们就处于这个时代，并且Spring4.x和Spring boot都推荐使用java配置的方式。 

```
Spring 		1.X  使用基本的框架类及配置文件（.xml）实现对象的声明及对象关系的整合。  org.springframework.core.io.ClassPathResource  org.springframework.beans.factory.xml.Xm**l****BeanFactory**  org.springframework.context.support.ClassPathXmlApplicationContext 		 		 	

Spring 		2.X  使用注解代替配置文件中对象的声明。简化配置。  org.springframework.stereotype.@Component  org.springframework.stereotype.@Controller  org.springframework.stereotype.@Service  org.springframework.stereotype.@Repository  org.springframework.stereotype.@Scope  org.springframework.beans.factory.annotation.@Autowired 		 		 		

Spring 		3.X  使用更强大的注解完全代替配置文件。  org.springframework.context.annotation.AnnotationConfigApplicationContext  org.springframework.context.annotation.@Configuration  org.springframework.context.annotation.@Bean  org.springframework.context.annotation.@Value  org.springframework.context.annotation.@Import 		 		 		

Spring 		4.X  使用条件注解强化之前版本的注解。  org.springframework.context.annotation.@Conditional 		 		 	
```

##### 2.3.4 Spring作者

​			Rod 		Johnson在2002年编著的《Expert 		one on one J2EE design and development》一书中，对Java 		EE 系统框架臃肿、低效、脱离现实的种种现状提出了质疑，并积极寻求探索革新之道。 		以此书为指导思想，他编写了interface21框架，这是一个力图冲破J2EE传统开发的困境，从实际需求出发，着眼于轻便、灵巧，易于开发、测试和部署的轻量级开发框架。 		Spring框架即以interface21框架为基础，经过重新设计，并不断丰富其内涵，于2004年3月24日，发布了1.0正式版。 		同年他又推出了一部堪称经典的力作《Expert 		one-on-one J2EE Development without 		EJB》，该书在Java世界掀起了轩然大波，不断改变着Java开发者程序设计和开发的思考方式。 		在该书中，作者根据自己多年丰富的实践经验，对EJB的各种笨重臃肿的结构进行了逐一的分析和否定，并分别以简洁实用的方式替换之。 		至此一战功成，Rod 		Johnson成为一个改变Java世界的大师级人物。 	

##### Spring和SpringMVC以及SpringBoot的区别

Spring 是一个开源框架，为简化企业级应用开发而生。Spring 可以是使简单的 JavaBean 实现以前只有 EJB 才能
实现的功能。Spring 是一个 IOC 和 AOP 容器框架。
Spring 容器的主要核心是：
控制反转（IOC），传统的 java 开发模式中，当需要一个对象时，我们会自己使用 new 或者 getInstance 等直接
或者间接调用构造方法创建一个对象。而在 spring 开发模式中，spring 容器使用了工厂模式为我们创建了所需要的对
象，不需要我们自己创建了，直接调用 spring 提供的对象就可以了，这是控制反转的思想。
依赖注入（DI），spring 使用 javaBean 对象的 set 方法或者带参数的构造方法为我们在创建所需对象时将其属
性自动设置所需要的值的过程，就是依赖注入的思想。
面向切面编程（AOP），在面向对象编程（oop）思想中，我们将事物纵向抽成一个个的对象。而在面向切面编程
中，我们将一个个的对象某些类似的方面横向抽成一个切面，对这个切面进行一些如权限控制、事物管理，记录日志等
公用操作处理的过程就是面向切面编程的思想。AOP 底层是动态代理，如果是接口采用 JDK 动态代理，如果是类采用
CGLIB 方式实现动态代理。

而SpringMVC是SpringMVC是基于Spring功能之上添加的Web框架，想用SpringMVC必须先依赖Spring。 

SpringMVC是一个类似于struts的MVC模式的WEB开发框架;

Spring是一个通用解决方案, 最大的用处就是通过Ioc/AOP解耦, 降低软件复杂性, 所以Spring可以结合SpringMVC等很多其他解决方案一起使用, 不仅仅只适用于WEB开发

SpringBoot不是Spring官方的框架模式，而是一个团队在Spring4.0版本上二次开发并开源公布出来的。简而言之，SpringBoot就是一个轻量级，简化配置和开发流程的web整合框架，我们可以说是因为SpringBoot才有了Spring这么火。

那么SpringBoot和Spring有什么区别呢？

    Spring Boot可以建立独立的Spring应用程序；
    内嵌了如Tomcat，Jetty和Undertow这样的容器，也就是说可以直接跑起来，用不着再做部署工作了；
    无需再像Spring那样搞一堆繁琐的xml文件的配置；
    可以自动配置(核心)Spring。SpringBoot将原有的XML配置改为Java配置，将bean注入改为使用注解注入的方式(@Autowire)，并将多个xml、properties配置浓缩在一个appliaction.yml配置文件中。
    提供了一些现有的功能，如量度工具，表单数据验证以及一些外部配置这样的一些第三方功能；
    整合常用依赖（开发库，例如spring-webmvc、jackson-json、validation-api和tomcat等），提供的POM可以简化Maven的配置。当我们引入核心依赖时，SpringBoot会自引入其他依赖。

------------------------------------------------

版权声明：本文为CSDN博主「qq_1959227206」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/yjt520557/java/article/details/88115402

#### 2.4 自动创建一个Spring Boot_HelloWorld（必须联网）

1. 打开IDEA，点击 +Create New Project. 开始创建一个新项目。

　　![img](pic/1156797-20190621123538157-722067721.png)

 

2. 在左侧菜单找到并点击 Spring Initializr，点击next。注意，这里idea默认使用https://start.spring.io提供的在线模板，所以需要保证网络畅通。

当然也可以选择下面的Custom从指定的链接加载模板。

​    这时，就有小朋友要问了。要是没网不就GG了，我还是用eclipse吧。放心，IDEA不可能这么菜。如何在本地搭建spring Initializr服务器，

请自行百度。后面会写一篇教程，先在这里立个flag吧。

![img](pic/1156797-20190621125349306-2101385514.png)

 

3.按实际情况依次填写项目信息。其中Type属性可以下拉选择project或者pom，Packaging属性可下拉选择jar

![img](pic/1156797-20190621125631973-1678172571.png)

 

4.最激动人心的界面来了！！！你可以从左面选择大类，然后在窗口中间勾选需要的依赖。右边可以看到已选择的依赖项。

上边下拉框可以选择Spring Boot的版本，这里使用最新版2.2.0 M4。完成后点击 Next。

这里我选择了“Web”类别下的“Spring Web Starter”、“Template”类别下的“Thymeleaf”以及“SQL”类别下的“Spring Data JPA”和“Mysql Driver”。

![img](pic/1156797-20190621134940954-236160325.png)   ![img](pic/1156797-20190621135708955-86527196.png)

 

5. 终于，最后一步了。设置项目名称Project name 和 工程保存路径 Project location。完成后，点击 Finish。

 ![img](pic/1156797-20190621140712395-150200200.png)

 

 6.等待IDEA构建好项目后，项目结构如下图所示。根据每个人在第4步选择的依赖不同，目录结构大同小异。

![img](pic/1156797-20190621141758330-880367033.png)

 

 7.再看看pom.xml，我们需要的依赖都静静的躺在里面。是不是so easy，妈妈再也不用担心我找依赖了。

 ![img](pic/1156797-20190621142401315-70906636.png)

 

 8.写个简单页面试试新建的工程好不好使。

> spring boot，启动。

![img](pic/1156797-20190621145900048-1241702910.png)

 

   9.访问看看效果如何，http://localhost:8080 

![img](pic/1156797-20190621150229002-490214384.png)

### 3. SpringBoot项目整合案例

- @ComponentScan注解:

  用来设置自动扫描的包,如果没有指定basePackage属性,默认扫描当前类所在的包及子包. 

  但其实新版本的springboot的@SpringBootApplication会自动扫描

  ```java
  @SpringBootApplication
  public class SpringbootApplication {
  
      public static void main(String[] args) {
          SpringApplication.run(SpringbootApplication.class, args);
      }
  }
  ```

- @RestController 注解

  ```java
  /**
   * @RestController = @Controller + @ResponseBody
   */
  @RestController
  //@Controller
  public class EmployeeHandler {
  
  //    @ResponseBody
      @RequestMapping("/getEmp")
      public Object getEmployee(){
          //创建一个Map
          Map<String, Object> map = new HashMap<>();
          //向map中放Employee对象
          map.put("emp",new Employee(1,"潘金莲","pjl@xmq.com",new Department(1001,"外交部")));
          return map;
      }
  }
  ```

# Linux

### 1. Linux文件与目录结构

#### Linux文件

Linux系统中一切皆文件。

#### Linux目录结构

![img](pic/003vPl7Rty6E8kZRlAEdc690.jpg)

==**/bin**==：
 bin是Binary的缩写, 这个目录存放着最经常使用的命令。

**/sbin**：
 s就是Super User的意思，这里存放的是系统管理员使用的系统管理程序。

**==/home==**：
用户的主目录，在Linux中，每个用户都有一个自己的目录，一般该目录名是以用户的账号命名的。

==**/root**==：
该目录为系统管理员，也称作超级权限者的用户主目录。

**==/boot==：**
这里存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件。

**/dev ：**
dev是Device(设备)的缩写, 该目录下存放的是Linux的外部设备，在Linux中访问设备的方式和访问文件的方式是相同的。

**==/etc==：**
这个目录用来存放所有的系统管理所需要的配置文件和子目录。

==**/lib**==：
这个目录里存放着系统最基本的动态连接共享库，其作用类似于Windows里的DLL文件。几乎所有的应用程序都需要用到这些共享库。

**/lost+found**：
这个目录一般情况下是空的，当系统非法关机后，这里就存放了一些文件。

**==/media==**：
 linux系统会自动识别一些设备，例如U盘、光驱等等，当识别后，linux会把识别的设备挂载到这个目录下。

**==/mnt==**：
系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在/mnt/上，然后进入该目录就可以查看光驱里的内容了。

**==/opt==**：
 这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库则就可以放到这个目录下。默认是空的。

**/proc**：
这个目录是一个虚拟的目录，它是系统内存的映射，我们可以通过直接访问这个目录来获取系统信息。
这个目录的内容不在硬盘上而是在内存里，我们也可以直接修改里面的某些文件，比如可以通过下面的命令来屏蔽主机的ping命令，使别人无法ping你的机器：



**/selinux**：
 这个目录是Redhat/CentOS所特有的目录，Selinux是一个安全机制，类似于windows的防火墙，但是这套机制比较复杂，这个目录就是存放selinux相关的文件的。

**/srv**：
 该目录存放一些服务启动之后需要提取的数据。

**/sys**：

 这是linux2.6内核的一个很大的变化。该目录下安装了2.6内核中新出现的一个文件系统 sysfs 。

sysfs文件系统集成了下面3种文件系统的信息：针对进程信息的proc文件系统、针对设备的devfs文件系统以及针对伪终端的devpts文件系统。

该文件系统是内核设备树的一个直观反映。

当一个内核对象被创建的时候，对应的文件和目录也在内核对象子系统中被创建。

**/tmp**：
这个目录是用来存放一些临时文件的。

==**/usr**==：
 这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似于windows下的program files目录。

**/usr/bin：**
系统用户使用的应用程序。

**/usr/sbin：**
超级用户使用的比较高级的管理程序和系统守护程序。

**/usr/src：**
内核源代码默认的放置目录。

**==/var==**：
这个目录中存放着在不断扩充着的东西，我们习惯将那些经常被修改的目录放在这个目录下。包括各种日志文件。

**/run**：
是一个临时文件系统，存储系统启动以来的信息。当系统重启时，这个目录下的文件应该被删掉或清除。如果你的系统上有 /var/run 目录，应该让它指向 run。

### 2. VI/VIM编辑器

- VI是Unix操作系统和类Unix操作系统中最通用的文本编辑器。

- VIM编辑器是从VI发展出来的一个性能更强大的文本编辑器。可以主动的以==字体颜色==辨别语法的正确性，方便程序设计。VIM与VI编辑器完全兼容。

  ![img](pic/vi-vim-cheat-sheet-sch.gif)

#### 三种模式

##### 1. 一般模式

以vi打开一个档案就直接进入一般模式了（这是**默认的模式**）。在这个模式中， 你可以使用『上下左右』按键来移动光标，你可以使用『删除字符』或『删除整行』来处理档案内容， 也可以使用『复制、贴上』来处理你的文件数据。

| yy        | ==复制==游标所在的那一行(常用)                               |
| :-------- | ------------------------------------------------------------ |
| p, P      | p 为将已复制的数据==粘贴==在光标下一行，P 则为粘贴在游标上一行 |
| u         | ==撤销==上一步                                               |
| y数字y    | 复制多行。在行首输入: y想要复制的行数y,在想要粘贴处按p       |
| dd        | ==删除==光标所在的一整行                                     |
| x         | 向后删除一个字符 (相当于 [del] 按键)                         |
| X         | 向前删除一个字符(相当于 [backspace] 亦即是退格键) 	(常用) |
| yw        | 复制一个词                                                   |
| dw        | 删除一个词                                                   |
| shift+^   | 移动到行头                                                   |
| shift+$   | **移动到行尾**                                               |
| gg或者1+G | **移动到页头**                                               |
| G         | **移动到页尾**                                               |
| 数字+G    | **移动到目标行**                                             |
|           |                                                              |

##### 2. 编辑模式

在一般模式中可以进行删除、复制、粘贴等的动作，但是无法编辑文件内容！要等到你按下『i, I, o, O, a, A, r, R』等任何一个字母之后才会进入编辑模式。

注意了！通常在Linux中，按下这些按键时，在画面的左下方会出现『INSERT或 REPLACE』的字样，此时才可以进行编辑。而如果要回到一般模式时， 则必须要按下『Esc』这个按键即可退出编辑模式。

| 进入输入或取代的编辑模式 |                                                              |
| ------------------------ | ------------------------------------------------------------ |
| i, I                     | 进入输入模式(Insert mode)：  	i 为『从目前光标所在处输入』， I 为『在目前所在行的第一个非空格符处开始输入』。 	(常用) |
| a, A                     | 进入输入模式(Insert mode)：  	a 为『从目前光标所在的下一个字符处开始输入』， A 	为『从光标所在行的最后一个字符处开始输入』。(常用) |
| o, O                     | 进入输入模式(Insert mode)：  	这是英文字母 o 的大小写。o 为『在目前光标所在的下一行处输入新的一行』； 	O 为在目前光标所在处的上一行输入新的一行！(常用) |
| r, R                     | 进入取代模式(Replace mode)：  	r 只会取代光标所在的那一个字符一次；R会一直取代光标所在的文字，直到按下 	ESC 为止；(常用) |
| [Esc]                    | 退出编辑模式，回到一般模式中(常用)                           |

##### 3.指令模式

**在一般模式当中**，输入『 **: / ?**』3个中的任何一个按钮，就可以将光标移动到最底下那一行。

在这个模式当中， 可以提供你『搜寻资料』的动作，而读取、存盘、大量取代字符、离开 vi 、显示行号等动作是在此模式中达成的！

**基本语法**

| :w             | 写入/==保存==                                  |
| -------------- | ---------------------------------------------- |
| :!             | ==强制执行==                                   |
| :q             | ==离开== vi                                    |
| :wq            | 储存后离开，若为 :wq! 则为强制储存后离开       |
| **:wq!**       | 强制保存退出                                   |
| / 要查找的词   | n 查找下一个，N 往上查找                       |
| ? 要查找的词   | n是查找上一个，N是往下查找                     |
| :set nu        | 显示行号                                       |
| :set nonu      | 关闭行号                                       |
| ZZ（shift+zz） | 没有修改文件直接退出，如果修改了文件保存后退出 |

##### 模式间转换

![vim-vi-workmodel](pic/vim-vi-workmodel.png)



### 查看网络IP和网关



##### 设置

1. 停止Network-manager的服务

   ```shell
   $ sudo service network-manager stop
   ```

2. 设置IP地址

   ```shell
   #备份原有配置文件
   $ cp /etc/network/interfaces  /etc/network/interfacesbak   
   
   $ sudo vim /etc/network/interfaces
   
   #输入下面的设置
   auto eth0  #开机自动连接网络
   iface eth0 inet static   #static表示使用固定ip，dhcp表述使用动态ip
   address 192.168.1.10   #设置ip地址
   netmask 255.255.255.0  #设置子网掩码
   gateway 192.168.1.2    #设置网关
   ```

3. 设置DNS服务器

   ```shell
   #备份原有dns配置文件
   $ cp  /etc/resolv.conf   /etc/resolv.confbak    
   
   #编辑配置文件
   $ sudo vim /etc/resolv.conf
   
   #添加以下内容
   nameserver 114.114.114.114   #设置首选dns
   nameserver 8.8.8.8   #设置备用dns
   ```

4. 启动Network-manager的服务

```
sudo service network-manager start
```

5. ping

   ![ifconfig](pic/ifconfig.png)

   ping一下 wlp1s0 inet处的ip地址，看是否能通

### 修改主机名称

修改linux的主机映射文件（hosts文件）

（1）进入Linux系统查看本机的主机名。通过hostname命令查看

（2）如果感觉此主机名不合适，我们可以进行修改。通过编辑/etc/sysconfig/network文件

###关闭防火墙

- 基本语法

  > service 服务名 start		：开启服务
  >
  > service  服务名 stop		：关闭服务
  >
  > service  服务名 restart	：功能描述：重新启动服务
  >
  > service  服务名 status	 ：功能描述：查看服务状态

- chkconfig 设置后台服务的自启配置

  > chkconfig   		 ：查看所有服务器自启配置
  >
  > chkconfig 服务名 off   ：关掉指定服务的自动启动
  >
  > chkconfig 服务名 on   ：开启指定服务的自动启动
  >
  > chkconfig 服务名 --list	：查看服务开机启动状态

- 

![image-20200328195114196](pic/image-20200328195114196.png)

### Linux 常用命令

#### 1. man

man ：获得帮助信息

```shell
man [命令或配置文件]		（功能描述：获得帮助信息）
```

| 信息        | 功能                   |
| ----------- | ---------------------- |
| NAME        | 命令的名称和单行描述   |
| SYNOPSIS    | 怎样使用命令           |
| DESCRIPTION | 命令功能的深入讨论     |
| EXAMPLES    | 怎样使用命令的例子     |
| SEE ALSO    | 相关主题（通常是手册页 |

#### 2. help 获得shell内置命令的帮助信息

help 命令	（功能描述：获得shell内置命令的帮助信息）

#### 3. 常用快捷键

| ctrl + C | 停止进程                |
| -------- | ----------------------- |
| ctrl + L | 清屏；彻底清屏是：reset |
| ctrl+ Q  | 退出                    |

#### 4. 文件目录类命令

- pwd ：显示当前工作目录的绝对路径

- ls ：列出目录的内容

  > - -a ：全部的文件，连同隐藏档( 开头为 . 的文件) 一起列出来(常用)
  > - -l ：长数据串列出，包含文件的属性与权限等等数据；(常用)

- cd 切换目录

  > - cd ~或 cd：回到自己的家目录
  > - ==cd -==  ： 回到上一次所在目录
  > - cd ..  ：回到当前目录的上一级目录
  > - cd -P ：跳转到实际物理路径，而非快捷方式路径

- mkdir：创建一个新的目录

  > 参数-p ：创建多级目录

- rmdir：删除一个空的目录

- touch： 创建空文件

  > 可直接 `vim 文件名`  , 这样可以直接打开

- cp： 复制文件或目录

  > ```
  > cp [选项] source dest 				: 复制source文件到dest
  > ```
  >
  > 参数 -r ：递归复制整个文件夹

- rm： 移除文件或目录

  > ```
  > rm [选项] deleteFile			（功能描述：递归删除目录中所有内容）
  > ```
  >
  > > -r : ==递归删除目录==中所有内容
  > > -f : 强制执行删除操作，而不提示用于进行确认。
  > > -v :显示指令的详细执行过程

- mv : 移动文件与目录或重命名

- cat： 查看文件内容

  > -n ：显示所有行的行号，包括空行。

- more： 文件内容分屏查看器

  > more指令是一个基于VI编辑器的文本过滤器，它以全屏幕的方式按页显示文本文件的内容。more指令中内置了若干快捷键，详见操作说明。
  >
  > ```
  > more 要查看的文件
  > ```
  >
  > 操作说明：
  >
  > - 空白键 (space) ：代表向下翻一页；
  > - Enter：代表向下翻『一行』；
  > - q：代表立刻离开 more ，不再显示该文件内容。
  > - Ctrl+F：滚动一屏
  > - Ctrl+B：返回上一屏
  > - = ：输出当前行的行号
  > - :f ：输出文件名和当前行的行号

- less ：分屏显示文件内容

  less指令用来分屏查看文件内容，它的功能与more指令类似，但是比more指令更加强大，支持各种显示终端。less指令在显示文件内容时，并不是一次将整个文件加载之后才显示，而是根据显示需要加载内容，对于显示**大型文件具有较高的效率**。

  > ```
  > less 要查看的文件
  > ```
  >
  > - 空格键：翻动一页；
  > - [pagedown]：向下翻动一页
  > - [pageup]：向上翻动一页；
  > - /字串：向下搜寻『字串』的功能；n：向下查找；N：向上查找；
  > - ?字串 ：向上搜寻『字串』的功能；n：向上查找；N：向下查找；
  > - q：离开 less 

- echo：输出内容到控制台

  ```
  echo [选项] [输出内容]
  ```

  > -e： 支持反斜线控制的字符转换
  >
  > 转义字符：
  >
  > > - `\\`   : 输出\本身
  > > - \n：换行符
  > > - \t： 制表符，也就是Tab键

- head ：显示文件头部内容

  head用于显示文件的开头部分内容，默认情况下head指令显示文件的前10行内容。

  > ```
  > head 文件
  > ```
  >
  > > -n <行数> ：指定显示头部内容的行数
  > >
  > > ```
  > > head -n 5 文件      （功能描述：查看文件头5行内容，5可以是任意行数）
  > > ```

- tail :输出文件尾部内容
  tail用于输出文件中尾部的内容，默认情况下tail指令显示文件的后10行内容。

  > -n<行数> ：输出文件尾部n行内容
  > -f ：显示文件最新追加的内容，监视文件变化

- ==`>` ：覆盖 和 >> ：追加==

  > （1）ll >文件       ：列表的内容写入文件a.txt中（**覆盖写**）
  >
  > （2）ll >>文件	 ：列表的内容**追加**到文件aa.txt的末尾
  >
  > （3）cat 文件1 > 文件2	（功能描述：将文件1的内容覆盖到文件2）
  >
  > （4）echo “内容” >> 文件

- ln ：软链接
  软链接也成为符号链接，类似于windows里的==桌面快捷方式==，有自己的数据块，主要存放了链接其他文件的路径。

  > ```
  > ln -s [原文件或目录] [软链接名]	
  > ```
  >
  > 经验技巧
  >
  > > 删除软链接： rm -rf 软链接名，而不是rm -rf 软链接名/
  > >
  > > 查询：通过ll就可以查看，列表属性第1位是l，尾部会有位置指向。

- history： 查看已经执行过历史命令

#### 5. 时间日期类

- date [OPTION]... [+FORMAT]

> - -d<时间字符串> ：显示指定的“时间字符串”表示的时间，而非当前时间
>
> - -s<日期时间> ：设置系统日期时间
>
> - <+日期时间格式> ：指定显示时使用的日期时间格式
>
>   > - date								（功能描述：显示当前时间）
>   > - date +%Y					  （功能描述：显示当前年份）
>   > - date +%m					（功能描述：显示当前月份）
>   > - date +%d					 （功能描述：显示当前是哪一天）
>   > - date "+%Y-%m-%d %H:%M:%S"		（功能描述：显示年月日时分秒）

- cal： ==查看日历==

  ```
  cal ： 显示本月日历
  cal [年份]			：显示某年日历
  ```

#### 6. 用户管理命令

- useradd： 添加新用户

  ```
  useradd [选项]用户名
  ```

  > useradd -g 组名 用户名	（功能描述：添加新用户到某个组）

- passwd ：设置用户密码

  ```
  passwd 用户名
  ```

- id： 查看用户是否存在

  ```
  id 用户名
  ```

- cat  /etc/passwd： 查看创建了哪些用户

- su ：切换用户

  > su 用户名称 ：切换用户，只能获得用户的执行权限，不能获得环境变量
  >
  > su - 用户名称 ：切换到用户并获得该用户的环境变量及执行权限

- userdel： 删除用户

  > userdel 用户名：删除用户但保存用户主目录
  >
  > userdel -r 用户名：用户和用户主目录，都删除

- who ：查看登录用户信息

  > whoami：显示自身用户名称
  >
  > who am i：显示**登录用户**的用户名

- sudo ：设置普通用户具有root权限

- usermod ：修改用户

  > ```
  > usermod -g 用户组 用户名
  > ```
  >
  > -g : 修改用户的初始登录组，给定的组必须存在

  

#### 7. 用户组管理命令

- groupadd: 新增组

  ```
  groupadd 组名
  ```

- groupdel ：删除组

  ```
  groupdel 组名
  ```

- groupmod 修改组

  ```
  groupmod -n 新组名 老组名
  ```

- cat  /etc/group ：查看创建了哪些组

  

#### 8. 文件权限类

Linux系统是一种典型的多用户系统，不同的用户处于不同的地位，拥有不同的权限。为了保护系统的安全性，Linux系统对不同的用户访问同一文件（包括目录文件）的权限做了不同的规定。在Linux中我们可以使用ll或者ls -l命令来显示一个文件的属性以及文件所属的用户和组。

每个文件的属性由左边第一部分的10个字符来确定：

![363003_1227493859FdXT](pic/363003_1227493859FdXT.png)

##### 1. 位：

> - 0首位表示类型
>
>   > 在Linux中第一个字符代表这个文件是目录、文件或链接文件等等
>   >
>   > - \- ：文件
>   > - d： 代表目录
>   > - l： 链接文档(link file)；
>
> - 第1-3位确定属主（该文件的所有者）拥有该文件的权限。---User
>
> - 第4-6位确定属组（所有者的同组用户）拥有该文件的权限，---Group
>
> - 第7-9位确定其他用户拥有该文件的权限 ---Other



##### 2. rxw作用文件和目录的不同解释

- 作用到文件：

  > - [ r ]代表可读(read): 可以读取，查看
  > - [ w ]代表可写(write): 可以修改，但是**不代表可以删除该文件，删除一个文件的前提条件是对该文件所在的目录有写权限，才能删除该文件.**
  > - [ x ]代表可执行(execute):可以被系统执行

- 作用到目录：

  > - [ r ]代表可读(read): 可以读取，ls查看目录内容
  > - [ w ]代表可写(write): 可以修改，目录内创建+删除+重命名目录
  > - [ x ]代表可执行(execute):可以进入该目录

![image-20200328215637080](pic/image-20200328215637080.png)

如果查看到是文件：链接数指的是硬链接个数。创建硬链接方法：

```
ln [原文件] [目标文件]	
```

如果查看的是文件夹：链接数指的是子文件夹个数。

#####  3. chmod 改变权限

![image-20200328220059923](pic/image-20200328220059923.png)

第一种方式变更权限

```
chmod [{ugoa}{+-=}{rwx}] 文件或目录
```

> u:所有者 g:所有组 o:其他人 a:所有人(u、g、o的总和

第二种方式变更权限

```
chmod  [mode=421 ]  [文件或目录]
```

> r=0x100   w=0x010  x=0x001      rwx=4+2+1=7

##### 5. chown 改变所有者

```
chown [选项] [最终用户] [文件或目录]  ： 改变文件或者目录的所有者
```

> -R ：递归操作

##### chgrp 改变所属组

```
chgrp [最终用户组] [文件或目录]
```



#### 9. 文件查找类

- find ：查找文件或者目录

  find指令将从指定目录向下递归地遍历其各个子目录，将满足条件的文件显示在终端。

  ```
  find [搜索范围/路径] [选项]
  ```

  > - -name<查询方式> ：按照指定的文件名查找模式查找文件
  >
  >   ```shell
  >    find xiyou/ -name “*.txt”
  >   ```
  >
  > - -user<用户名> ：查找属于指定用户名所有文件
  >
  >   ```shell
  >   find xiyou/ -user cxy
  >   ```
  >
  > - -size<文件大小> ：按照指定的文件大小查找文件。
  >
  >   ```sh
  >   find /home -size +204800
  >   ```

- grep 过滤查找及“|”管道符

  管道符，“|”，表示==将前一个命令的处理结果输出传递给后面的命令处理==

  ```
  grep [选项 ] [查找内容] [源文件]
  ```

  > -n : 显示匹配行及行号。
  >
  > ```
  > ll  |  grep -n test
  > ```
  >
  > ==-r : 递归操作==

- which ：查找命令
  查找命令在==哪个目录下==

  ```
  which [命令]
  ```

#### 10. 压缩和解压类

- gzip/gunzip 压缩

  ```
  gzip [文件]	 ：压缩文件，只能将文件压缩为*.gz文件
  gunzip [文件.gz]	 ：解压缩文件命令
  ```

  > 经验技巧
  >
  > - **只能压缩文件**不能压缩目录
  >
  > - **不保留原来的文件**

- zip/unzip 压缩

  > ```
  > zip  [选项] [XXX.zip]  [将要压缩的内容] ：压缩文件和目录的命令）
  > ```
  >
  > > -r : 压缩目录
  >
  > ```
  > unzip [选项] [XXX.zip] ：解压缩文件）
  > ```
  >
  > > -d<目录> : 指定解压后文件的存放目录

  zip 压缩命令在window/linux都通用，可以压缩目录且保留源文件。

  

- ==tar 打包==

  > ```
  > tar  [选项] [XXX.tar.gz]  [将要打包进去的内容]：打包目录，压缩后的文件格式.tar.gz
  > ```
  >
  > - -z ：打包同时压缩
  >
  > - ==-c==：产生.tar打包文件
  >
  > - -v ：显示详细信息
  >
  > - -f：指定压缩后的文件名
  >
  > - ==-x==：解包.tar文件
  >
  >   ```shell
  >   #可将多个文件或目录打包，放在后面用空格隔开即可
  >   tar -zcvf xiyou.tar.gz xiyou/ xiyou/
  >   
  >   #解压到当前目录
  >   tar -zxvf houma.tar.gz
  >   #解压到其它路径，需加 -C
  >   tar -zxvf xiyou.tar.gz -C /opt
  >   ```

  

#### 11. 磁盘分区类

- df : 查看磁盘空间使用情况 

  ```
  df  [选项]
  ```

  > -h : 以人们较易阅读的 GBytes, MBytes, KBytes 等格式自行显示；

-  fdisk :查看分区 

   > -l : 显示所有硬盘的分区列表

- mount/umount :挂载/卸载

  对于Linux用户来讲，不论有几个分区，分别分给哪一个目录使用，它总归就是一个根目录、一个独立且唯一的文件结构。

  Linux中每个分区都是用来组成整个文件系统的一部分，它在用一种叫做“挂载”的处理方法，它整个文件系统中包含了一整套的文件和目录，并将一个分区和一个目录联系起来，要载入的那个分区将使它的存储空间在这个目录下获得。

  > ```
  > mount [-t vfstype] [-o options] [device dir ]：挂载设备
  > umount [设备文件名或挂载点] ：卸载设备
  > ```
  >
  > > - -t vfstype: 指定文件系统的类型，通常不必指定。mount 会自动选择正确的类型。常用类型有：
  > >
  > >   > - 光盘或光盘镜像：iso9660
  > >   > - DOS fat16文件系统：msdos
  > >   > - Windows 9x fat32文件系统：vfat
  > >   > - Windows NT ntfs文件系统：ntfs
  > >   > - Mount Windows文件网络共享：smbfs
  > >   > - UNIX(LINUX) 文件网络共享：nfs
  > >
  > > - -o options : 主要用来描述设备或档案的挂接方式。常用的参数有：
  > >
  > >   > - loop：用来把一个文件当成硬盘分区挂接上系统
  > >   > - ro：采用只读方式挂接设备
  > >   > - rw：采用读写方式挂接设备
  > >   > - iocharset：指定访问文件系统所用字符集
  > >
  > > - device : 要挂接(mount)的设备
  > >
  > > - dir :设备在系统上的挂接点(mount point)

  

#### 12. 进程线程类

进程是正在执行的一个程序或命令，每一个进程都是一个运行的实体，都有自己的地址空间，并占用一定的系统资源。

- ps :查看当前系统进程状态

  > ```
  > ps aux  | grep xxx	：查看系统中所有进程
  > ```
  >
  > > -a : 选择所有进程
  > > -u : 显示所有用户的所有进程
  > > -x :显示没有终端的进程
  >
  > ps aux显示信息说明:
  >
  > > - USER：该进程是由哪个用户产生的
  > > - PID：进程的ID号
  > > - %CPU：该进程占用CPU资源的百分比，占用越高，进程越耗费资源；
  > > - %MEM：该进程占用物理内存的百分比，占用越高，进程越耗费资源；
  > > - VSZ：该进程占用虚拟内存的大小，单位KB；
  > > - RSS：该进程占用实际物理内存的大小，单位KB；
  > > - TTY：该进程是在哪个终端中运行的。其中tty1-tty7代表本地控制台终端，tty1-tty6是本地的字符界面终端，tty7是图形终端。pts/0-255代表虚拟终端。
  > > - STAT：进程状态。常见的状态有：R：运行、S：睡眠、T：停止状态、s：包含子进程、+：位于后台
  > > - START：该进程的启动时间
  > > - TIME：该进程占用CPU的运算时间，注意不是系统时间
  > > - COMMAND：产生此进程的命令名
  >
  > ```
  > ps -ef | grep xxx ：可以查看子父进程之间的关系
  > ```
  >
  > ps -ef显示信息说明: 
  >
  > > UID：用户ID
  > >
  > > PID：进程ID
  > >
  > > PPID：父进程ID
  > >
  > > C：CPU用于计算执行优先级的因子。数值越大，表明进程是CPU密集型运算，执行优先级会降低；数值越小，表明进程是I/O密集型运算，执行优先级会提高
  > >
  > > STIME：进程启动的时间
  > >
  > > TTY：完整的终端名称
  > >
  > > TIME：CPU时间
  > >
  > > CMD：启动进程所用的命令和参数


- kill :终止进程

```
kill  [选项] 进程号 ：通过进程号杀死进程
killall 进程名称 ：通过进程名称杀死进程，也支持通配符，这在系统因负载过大而变得很慢时很有用
```

> -9 ：表示强迫进程立即停止

- pstree 查看进程树

```
pstree [选项]
```

> -p：显示进程的PID 
> -u：显示进程的所属用户

- top 查看系统健康状态

```
top [选项]	
```

> -d 秒数 ：指定top命令每隔几秒更新。默认是3秒在top命令的交互模式当中可以执行的命令
>
> -i：使top不显示任何闲置或者僵死进程。
> -p：通过指定监控进程ID来仅仅监控某个进程的状态。

操作说明

> | 操作 | 功能                          |
> | ---- | ----------------------------- |
> | P    | 以CPU使用率排序，默认就是此项 |
> | M    | 以内存的使用率排序            |
> | N    | 以PID排序                     |
> | q    | 退出top                       |



查询结果字段解释

第一行信息为任务队列信息

第二行为进程信息

第三行为CPU信息

- netstat: 显示网络统计信息和端口占用情况

```
	netstat -anp |grep 进程号	（功能描述：查看该进程网络信息）
	netstat -nlp	| grep 端口号	（功能描述：查看网络端口号占用情况）
```

> -n: 拒绝显示别名，能显示数字的全部转化成数字
> -l：仅列出有在listen（监听）的服务状态
> -p：表示显示哪个进程在调用

#### 13. crond：服务管理

重新启动crond服务

```
service crond restart
```

##### crontab 定时任务设置

```
crontab [选项]
```

> -e: 编辑crontab定时任务
> -l：查询crontab任务
> -r：删除当前用户所有的crontab任务

参数说明:

> 1. `crontab -e` 进入crontab编辑界面。会打开vim编辑你的工作。
>
>    \* * * * * 执行的任务
>
>    > | 项目    | 含义                     | 范围                    |
>    > | ------- | ------------------------ | ----------------------- |
>    > | 第一个* | 一小时当中的第几==分==钟 | 0-59                    |
>    > | 第二个* | 一天当中的第几小==时==   | 0-23                    |
>    > | 第三个* | 一个月当中的第几==天==   | 1-31                    |
>    > | 第四个* | 一年当中的第几==月==     | 1-12                    |
>    > | 第五个* | 一周当中的==星期==几     | 0-7（0和7都代表星期日） |
>
> 2. 特殊符号
>
>    | *    | 代表任何时间。比如第一个“*”就代表一小时中每分钟都执行一次的意思 |
>    | ---- | ------------------------------------------------------------ |
>    | ，   | 代表不连续的时间。比如“0 8,12,16 * * * 命令”，就代表在每天的8点0分，12点0分，16点0分都执行一次命令 |
>    | -    | 代表连续的时间范围。比如“0 5  *  *  1-6命令”，代表在周一到周六的凌晨5点0分执行命令 |
>    | */n  | 代表每隔多久执行一次。比如“*/10  *  *  *  *  命令”，代表每隔10分钟就执行一遍命令 |
>
> 3. 特定时间执行命令
>
>    | 命令         | 含义                                       |
>    | ------------ | ------------------------------------------ |
>    | 45 22 * * *  | 在22点45分执行命令                         |
>    | 0 17 * * 1   | 每周1 的17点0分执行命令                    |
>    | 0 5 1,15 * * | 每月1号和15号的凌晨5点0分执行命令          |
>    | 40 4 * * 1-5 | 每周一到周五的凌晨4点40分执行命令          |
>    | */10 4 * * * | 每天的凌晨4点，每隔10分钟执行一次命令      |
>    | 0 0 1,15 * 1 | 每月1号和15号，每周1的0点0分都会执行命令。 |
>
>    ------
>
>    注意：星期几和几号最好不要同时出现，因为他们定义的都是天。非常容易让管理员混乱。
>
>    ```shell
>    # 每隔1分钟，向/root/bailongma.txt文件中添加一个11的数字
>    */1 * * * * /bin/echo ”11” >> /root/bailongma.txt
>    ```

#### 14. 软件包管理

##### RPM

RPM（RedHat Package Manager），RedHat软件包管理工具，类似windows里面的setup.exe

 是Linux这系列操作系统里面的打包安装工具，它虽然是RedHat的标志，但理念是通用的。

RPM包的名称格式：

```
Apache-1.3.23-11.i386.rpm

apache ： 软件名称
1.3.23-11：软件的版本号，主版本和此版本
i386：是软件所运行的硬件平台，Intel 32位微处理器的统称
rpm：文件扩展名，代表RPM包
```

- RPM查询命令（rpm -qa）

  ```
  rpm -qa	：查询所安装的所有rpm软件包
  rpm -qa | grep [rpm软件包]：查询和筛选所安装的rpm软件包
  ```

- RPM卸载命令（rpm -e）

  ```
  rpm -e [选项]
  ```

  > -e：卸载软件包
  > --nodeps：卸载软件时，不检查依赖。这样的话，那些使用该软件包的软件在此之后可能就不能正常工作了。

- RPM安装命令（rpm -ivh）

  ```
  rpm [选项] [RPM包全名]
  ```

  > -i：-i=install，安装
  > -v：-v=verbose，显示详细信息
  > -h：-h=hash，进度条
  > --nodeps：--nodeps，不检测依赖进度

- 

##### YUM仓库配置

YUM（全称为 ==Yellow dog Updater, Modified==）是一个在Fedora和RedHat以及CentOS中的Shell前端软件包管理器。基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包，无须繁琐地一次次下载、安装

![image-20200329232335223](pic/image-20200329232335223.png)

**常用命令**

```
yum [选项] [参数]
```

> 选项说明：
>
> > -y：对所有提问都回答“yes”
>
> 参数说明：
>
> > install：安装rpm软件包
> > update：更新rpm软件包
> > check-update：检查是否有可用的更新rpm软件包
> >
> > remove：删除指定的rpm软件包
> > list：显示软件包信息
> > clean：清理yum过期的缓存
> > deplist：显示yum软件包的所有依赖关系



# Redis

### NoSQL

![image-20200404213118717](pic/image-20200404213118717.png)

![image-20200404213128431](pic/image-20200404213128431.png)

![image-20200404213149223](pic/image-20200404213149223.png)

![image-20200404213207361](pic/image-20200404213207361.png)

![image-20200404213230259](pic/image-20200404213230259.png)

![image-20200404213251104](pic/image-20200404213251104.png)

![image-20200404213306419](pic/image-20200404213306419.png)

![image-20200404213320569](pic/image-20200404213320569.png)

![image-20200404213340491](pic/image-20200404213340491.png)

![image-20200404213402674](pic/image-20200404213402674.png)

![image-20200404213433609](pic/image-20200404213433609.png)

![image-20200404213622485](pic/image-20200404213622485.png)

![image-20200404213642289](pic/image-20200404213642289.png)

![image-20200404213654466](pic/image-20200404213654466.png)

### Redius 简介

​	Redis是一个开源的key-value存储系统。和Memcached类似，它支持存储的value类型相对更多，包括string(字符串)、list(链表)、set(集合)、zset(sorted set --有序集合)和hash（哈希类型）。这些数据类型都支持push/pop、add/remove及取交集并集和差集及更丰富的操作，而且这些操作都是原子性的。在此基础上，Redis支持各种不同方式的排序。与memcached一样，为了保证效率，数据都是缓存在内存中。区别的是Redis会周期性的把更新的数据写入磁盘或者把修改操作写入追加的记录文件，并且在此基础上实现了master-slave(主从)同步。

redis端口: 6379

和Memcached的区别:

1. Memcached不支持持久化,Redius支持持久化

   ![image-20200404214013342](pic/image-20200404214013342.png)

2. Memcached只支持简单的key-value存储,Redius还支持string、list、set、zset(sorted set --有序集合)和hash类型

3. Memcached: 串行 vs 多线程+锁 

   Redius :单线程+多路IO复用

   ![image-20200404214326111](pic/image-20200404214326111.png)

   

###  Redis的基本使用

#### 1. 启动与关闭

```shell
#启动命令
$ redis-server

#进入Redius
$ redis-cli

#单实例关闭
#未进入Redius 关闭
$ redis-cli shutdown
#已进入Redius 关闭
```

#### 2. Redis的数据类型

![image-20200404215721364](pic/image-20200404215721364.png)

##### 1. Key

- ==keys  *==  

  >  查询当前库的所有key

- ==exists==  <key>

  > 判断某个key是否存在

- ==type==  <key>

  > 查看key的类型

- ==del==  <key>

  > 删除某个key

- ==expire==   <key>   <seconds>

  > 为key设置过期时间，单位秒

- ==ttl==   <key>

  > 查看还有多少秒过期，**-1**表示永不过期，**-2**表示已过期

- ==dbsize==

  > 查看当前数据库的key的数量

- ==flushdb==

  > 清空当前库

- ==flushall==

  > 通杀全部库

##### 2. String

> - String是Redis最基本的类型，你可以理解成与Memcached一模一样的类型，一个key对应一个value。
> - String类型是二进制安全的。意味着Redis的string可以包含任何数据。比如jpg图片或者序列化的对象 。
> - String类型是Redis最基本的数据类型，一个Redis中字符串value最多可以是512M



- ==get==   <key>

  >  查询对应键**值**

- ==set==   <key>  <value>

  > 添加键值对

- ==append==  <key>  <value>

  > 将给定的<value> 追加到原值的末尾

- ==strlen==  <key>

  > 获得值的长度

- ==setnx==  <key>  <value>

  > 只有在 key 不存在时设置 key 的值

- ==incr==  <key>

  > 将 key 中储存的数字值增1
  > 只能对数字值操作，如果为空，新增值为1

- ==decr==  <key>

  > 将 key 中储存的数字值减1
  > 只能对数字值操作，如果为空，新增值为-1

- ==incrby / decrby== <key>  <步长>

  > 将 key 中储存的数字值增减。自定义步长

- ==mset==  <key1>  <value1>  <key2>  <value2>  .....   <key>

  >  同时设置一个或多个 key-value对

- ==mget==  <key1>   <key2>   <key3> ....

  > 同时获取一个或多个 value

- ==msetnx== <key1>  <value1>  <key2>  <value2>  ..... 

  > 获得值的长度

- ==getrange== <key>  <起始位置>  <结束位置>

  > 获得值的范围，类似java中的substring

- ==setrange== <key>  <起始位置>  <value>

  > 用 <value>  覆写<key> 所储存的字符串值，从<起始位置>开始

- ==setex==  <key>  <过期时间>   <value>

  > 设置键值的同时，设置过期时间，单位秒

- ==getset== <key>  <value>

  > 以新换旧，设置了新值同时获得旧值

![image-20200404223640487](pic/image-20200404223640487.png)

##### 3.list

![image-20200405172510948](pic/image-20200405172510948.png)

- ==lpush/rpush==  <key>  <value1>  <value2>  <value3> ....

  >  从左边/右边插入一个或多个==值==

- ==lpop/rpop==  <key> 

  > 从左边/右边吐出一个值
  >
  > ==值在键在，值亡键亡==

- ==rpoplpush==<key1>  <key2>

  > 从<key1>列表右边吐出一个值，插到<key2>列表左边

- ==lrange== <key> <start> <stop>

  > 按照索引下标获得元素(从左到右)

- ==lindex== <key> <index>

  > 按照索引下标获得元素(从左到右)

- ==llen== <key>

  > 获得列表长度

- ==linsert== <key>  ==before== <value>  <newvalue>   

  > 在<value>的前面插入<newvalue> 

-  ==lrem== <key> <n>  <value>

   > 从左边删除n个value(从左到右)

   


##### 4.set

![image-20200405183347133](pic/image-20200405183347133.png)

- ==sadd== <key>  <value1>  <value2> .....  

- > 将一个或多个 member 元素加入到集合 key 当中，已经存在于集合的 member 元素将被忽略

- ==smembers== <key>

  > 取出该集合的所有值

- ==sismember== <key>  <value>   

  > 判断集合<key>是否为含有该<value>值，有返回1，没有返回0

- ==scard==   <key>  

  > 返回该集合的元素个数

- ==srem== <key> <value1> <value2> ....

  > 删除集合中的某个元素

- ==spop== <key> 

  > 随机从该集合中吐出一个值

- ==srandmember== <key> <n>

  > 随机从该集合中取出n个值。
  > 不会从集合中删除

- ==sinter==<key1> <key2>  

  > 返回两个集合的交集元素

- ==sunion==<key1> <key2>   

  > 返回两个集合的并集元素

- ==sdiff==<key1> <key2>  

  > 返回两个集合的差集元素



##### 5. hash

- Redis  hash 是一个键值对集合。
- Redis hash是一个string类型的field和value的映射表，hash特别适合用于存储对象。
- 类似Java里面的Map<String,Object>

![image-20200405183546018](pic/image-20200405183546018.png)

- ==hset== <key>  <field>  <value> 

  >  给<key>集合中的  <field>键赋值<value>

- ==hget== <key1>  <field>

  > 从<key1>集合<field> 取出 value 

- ==hmset== <key1>  <field1> <value1> <field2> <value2>...  

  > 批量设置hash的值

- ==hexists key==  <field>

  > 查看哈希表 key 中，给定域 field 是否存在

- ==hkeys== <key>  

  > 列出该hash集合的所有field

- ==hvals== <key>

  > 列出该hash集合的所有value

- ==hincrby== <key> <field>  <increment>

  > 为哈希表 key 中的域 field 的值加上增量 increment

- ==hsetnx== <key>  <field> <value>

  > 将哈希表 key 中的域 field 的值设置为 value ，当且仅当域 field 不存在 

  


##### 5. zset(sorted set)

​		Redis有序集合zset与普通集合set非常相似，是一个没有重复元素的字符串集合。不同之处是有序集合的所有成员都关联了一个评分（score） ，这个评分（score）被用来按照从最低分到最高分的方式排序集合中的成员。集合的成员是唯一的，但是评分可以是重复了 。

​		因为元素是有序的, 所以你也可以很快的根据评分（score）或者次序（position）来获取一个范围的元素。访问有序集合的中间元素也是非常快的,因此你能够使用有序集合作为一个没有重复成员的智能列表



- ==zadd==  <key> <score1> <value1>  <score2> <value2>…

- ==zrange== <key>  <start> <stop>  [WITHSCORES] 

  > 返回有序集 key 中，下标在<start> <stop>之间的元素
  > 带WITHSCORES，可以让分数一起和值返回到结果集

- ==zrangebyscore key min max== [withscores] [limit offset count]

  > 返回有序集 key 中，所有 score 值介于 min 和 max 之间(包括等于 min 或 max )的成员。有序集成员按 score 值递增(从小到大)次序排列

- ==zrevrangebyscore key max min== [withscores] [limit offset count]

  > 同上，改为从大到小排列

- ==zincrby== <key> <increment> <value>

  > 为元素的score加上增量

- ==zrem==  <key>  <value>

  > 删除该集合下，指定值的元素 

- ==zcount== <key>  <min>  <max> 

  > 统计该集合，分数区间内的元素个数

-  ==zrank== <key>  <value>

   > 返回该值在集合中的排名，从0开始

   

#### 3. Java的Redis客户端Jedis

1. [创建Maven版的Java工程](#1.创建Maven版的Java工程)

2. 加入依赖

   ```xml
   			<dependency>
               <groupId>redis.clients</groupId>
               <artifactId>jedis</artifactId>
               <version>2.9.0</version>
           </dependency>
   ```

3. 在终端中打开redis

   ```shell
   $ redis-server
   ```

4. 测试链接

   ```java
   public class Demo01 {
       public static void main(String[] args) {
           //连接本地的 Redis 服务
           Jedis jedis = new Jedis("127.0.0.1",6379);
           //查看服务是否运行，打出pong表示OK
           System.out.println("connection is OK==========>: " + jedis.ping());
       }
   }
   ```

5. 其它操作

   ```java
   				//向Jedis中添加String类型的数据
           jedis.set("k5","v5");
           String k5 = jedis.get("k5");
           System.out.println("k5对应的值是:" + k5);
   
           //获取redis中所有key
           Set<String> keys = jedis.keys("*");
           for (String key : keys){
               System.out.println(key);
           }
           jedis.close();
   ```

###  Redis事务

![image-20200406161808848](pic/image-20200406161808848.png)

![image-20200406161819866](pic/image-20200406161819866.png)

![image-20200406161841812](pic/image-20200406161841812.png)

![image-20200406170235021](pic/image-20200406170235021.png)

#### 1. 为什么要有事务

想想一个场景： 有很多人有你的账户,同时去参加双十一抢购

![image-20200406170844829](pic/image-20200406170844829.png)

#### 2. 悲观锁&乐观锁

==**悲观锁**==(Pessimistic Lock), 顾名思义，就是很悲观，每次去拿数据的时候都认为别人会修改，所以每次在拿数据的时候都会上锁，这样别人想拿这个数据就会block直到它拿到锁。**传统的关系型数据库里边就用到了很多这种锁机制**，比如行锁，表锁等，读锁，写锁等，都是在做操作之前先上

==**乐观锁**==(Optimistic Lock), 顾名思义，就是很乐观，每次去拿数据的时候都认为别人不会修改，所以不会上锁，但是在更新的时候会判断一下在此期间别人有没有去更新这个数据，可以使用版本号等机制。**乐观锁适用于多读的应用类型，这样可以提高吞吐量。Redis就是利用这种check-and-set机制实现事务的**

![image-20200406170900471](pic/image-20200406170900471.png)

##### 乐观锁的操作

![image-20200406171532936](pic/image-20200406171532936.png)

![image-20200406171551860](pic/image-20200406171551860.png)

#### 3. 事务的三特性

- 单独的隔离操作 
  事务中的所有命令都会序列化、按顺序地执行。事务在执行的过程中，不会被其他客户端发送来的命令请求所打断。

- 没有隔离级别的概念 
  队列中的命令没有提交之前都不会实际的被执行，因为事务提交前任何指令都不会被实际执行，也就不存在“事务内的查询要看到事务里的更新，在事务外查询不能看到”这个让人万分头痛的问题

- 不保证原子性 
  Redis同一个事务中如果有一条命令执行失败，其后的命令仍然会被执行，没有回滚 



###  Redis的持久化

![image-20200406200143749](pic/image-20200406200143749.png)

#### RDB

在指定的时间间隔内将内存中的数据集快照写入磁盘，也就是行话讲的Snapshot快照，它恢复时是将快照文件直接读到内存里。

**备份是如何执行的**:

Redis会单独创建（fork）一个子进程来进行持久化，会先将数据写入到一个临时文件中，待持久化过程都结束了，再用这个临时文件替换上次持久化好的文件。整个过程中，主进程是不进行任何IO操作的，这就确保了极高的性能如果需要进行大规模数据的恢复，且对于数据恢复的完整性不是非常敏感，那RDB方式要比AOF方式更加的高效。RDB的缺点是最后一次持久化后的数据可能丢失

**fork**:

   在Linux程序中，fork()会产生一个和父进程完全相同的子进程，但子进程在此后多会exec系统调用，出于效率考虑，Linux中引入了“写时复制技术”，一般情况父进程和子进程会共用同一段物理内存，只有进程空间的各段的内容要发生变化时，才会将父进程的内容复制一份给子进程

![image-20200406214120316](pic/image-20200406214120316.png)

修改rdb文件的快照保存地址:

```shell
/var/log/redis/redis-server.log
```



/var/lib/redis

![image-20200406214652432](pic/image-20200406214652432.png)

![image-20200406214702263](pic/image-20200406214702263.png)

![image-20200406214720533](pic/image-20200406214720533.png)



#### AOF

==以日志的形式来记录每个写操==作，将Redis执行过的所有写指令记录下来(读操作不记录)，只许追加文件但不可以改写文件，Redis启动之初会读取该文件重新构建数据，换言之，==Redis重启的话就根据日志文件的内容将写指令从前到后执行一次以完成数据的恢复工作==

![image-20200407172208570](pic/image-20200407172208570.png)

##### AOF和RDB同时开启，redis听谁的？

![image-20200407173145469](pic/image-20200407173145469.png)

![image-20200407173202838](pic/image-20200407173202838.png)

##### Rewrite

AOF采用文件追加方式，文件会越来越大为避免出现此种情况，新增了重写机制,当AOF文件的大小超过所设定的阈值时，Redis就会启动AOF文件的内容压缩，只保留可以恢复数据的最小指令集.可以使用命令bgrewriteaof

**Redis如何实现重写:**

AOF文件持续增长而过大时，会fork出一条新进程来将文件重写(也是先写临时文件最后再rename)，遍历新进程的内存中数据，每条记录有一条的Set语句。重写aof文件的操作，并没有读取旧的aof文件，而是将整个内存中的数据库内容用命令的方式重写了一个新的aof文件，这点和快照有点类似

![image-20200407174702809](pic/image-20200407174702809.png)

![image-20200407174747245](pic/image-20200407174747245.png)

### Redis的主从复制



![image-20200407175256095](pic/image-20200407175256095.png)

####一主二仆模式

 配置 : 配从(服务器)不配主(服务器)

- ==拷贝多个redis.conf文件include==
- 开启daemonize yes
- ==Pid文件名字pidfile==
- ==指定端口port==
- Log文件名字
- ==Dump.rdb名字dbfilename==
- Appendonly 关掉或者换名字



##### 一主二仆的演示

==先 `service redis stop`关闭redis==.conf对应的redis进程!!!  不然shutdown 6379时.,从机看到的主机状态仍然是up

新建conf文件,命名为: **redis6379.conf**,根据上面高亮部分,从主服务器配置文件中复制过来,将末尾改为如下:

```
include /etc/redis/redis.conf
pidfile /var/run/redis/redis6379.pid
port 6379
dbfilename dump6379.rdb
```

将redis6379.conf复制两份,命名为redis6380.conf, redis6381.conf. 并用如下语句将里面的6379全部重命名为对应的数字

```shell
:%s/6379/6380
:%s/6379/6381
```

开启三个终端 分别执行:

```shell
sudo redis-server redis6379.conf
redis-cli -p 6379
#打印主从复制的相关信息
127.0.0.1:6379> info replication
#主机写内容
127.0.0.1:6379> set k1 v1

$sudo redis-server redis6380.conf
$redis-cli -p 6380
127.0.0.1:6380> info replication
#"拜师", 请求变为6379的从机
127.0.0.1:6380> slaveof 127.0.0.1 6379
127.0.0.1:6380> info replication
#可以从主机读取key,但不可以写
127.0.0.1:6380> get k1


$sudo redis-server redis6381.conf
$redis-cli -p 6381
127.0.0.1:6381> info replication
#"拜师", 请求变为6379的从机
127.0.0.1:6381> slaveof 127.0.0.1 6379
127.0.0.1:6381> info replication
#可以从主机读取key,但不可以写
127.0.0.1:6381> get k1
```

**问题:**

1 切入点问题？slave1、slave2是从头开始复制还是从切入点开始复制?比如从k4进来，那之前的123是否也可以复制

> 答:从头开始复制

2 从机是否可以写？set可否？

> 答:不可以 

3 主机shutdown后情况如何？从机是上位还是原地待命

> 答:原地待命

4 主机又回来了后，主机新增记录，从机还能否顺利复制？

> 答:可以

5 其中一台从机down后情况如何？依照原有它能跟上大部队吗？

> 答: 不可以

![image-20200407220618686](pic/image-20200407220618686.png)

##### 复制原理

- 每次==从机联通==后，都会给主机发送sync指令

- 主机立刻进行存盘操作，发送RDB文件给从机

- 从机收到RDB文件后，进行全盘加载

- 之后每次==主机的写操作==，都会立刻发送给从机，从机执行相同的命令

  ![image-20200407220902085](pic/image-20200407220902085.png)

#### 薪火相传

上面这种模式,主机的压力太大

- 上一个slave可以是下一个slave的Master，slave同样可以接收其他slaves的连接和同步请求，那么该slave作为了链条中下一个的master, ==可以有效减轻master的写压力==,去中心化降低风险。

- 用 slaveof  <ip>  <port>

- 中途变更转向:会清除之前的数据，重新建立拷贝最新的

- **风险** : 一旦某个slave宕机，后面的slave都没法备份

  ![image-20200407221009618](pic/image-20200407221009618.png)

##### 规避风险: 反客为主

- 当一个master宕机后，后面的slave可以立刻升为master，其后面的slave不用做任何修改
- 用 `slaveof  no one`  ==将从机变为主机==(需手动输入该命令才能变为主机, 哨兵模式可自动监测,当主机down掉了, 会自动将一个从机变为主机)



#### 哨兵模式(sentinel)

反客为主的自动版，能够后台监控主机是否故障，如果故障了根据投票数自动将从库转换为主库

![image-20200407222453826](pic/image-20200407222453826.png)

##### 配置哨兵

- 在redis.conf中找到 `slave-priority 100` 语句,将其复制到待继位的从机的配置文件下,100改为10(值越小,优先级越高)

- 调整为一主二仆模式

- 自定义的 redis.conf 所在目录下新建 sentinel.conf 文件

  在配置文件中填写内容：

  ```
  sentinel  monitor  mymaster  127.0.0.1  6379  1
  ```

  其中mymaster为监控对象起的服务器名称， 1 为 至少有多少个哨兵同意迁移的数量

##### 启动哨兵

```shell
$ redis-sentinel  sentinel.conf
```

##### 故障恢复

![image-20200407222945490](pic/image-20200407222945490.png)



### redis的集群

1. 容量不够，redis如何进行扩容？
2. 并发写操作， redis如何分摊？



#### 1. 分布式与集群

![preview](pic/v2-e628e972ac34b597ba2c1f7f0d326705_r.jpg)

##### 单机结构

我想大家最最最熟悉的就是单机结构，一个系统业务量很小的时候所有的代码都放在一个项目中就好了，然后这个项目部署在一台服务器上就好了。整个项目所有的服务都由这台服务器提供。这就是单机结构。

那么，单机结构有啥缺点呢？我想缺点是显而易见的，单机的处理能力毕竟是有限的，当你的业务增长到一定程度的时候，单机的硬件资源将无法满足你的业务需求。此时便出现了集群模式，往下接着看。

##### 集群结构

集群模式在程序猿界有各种装逼解释，有的让你根本无法理解，其实就是一个很简单的玩意儿，且听我一一道来。

单机处理到达瓶颈的时候，你就把==单机复制几份==，这样就构成了一个“集群”。集群中每台服务器就叫做这个集群的一个“节点”，所有节点构成了一个集群。每个节点都提供相同的服务，那么这样系统的处理能力就相当于提升了好几倍（有几个节点就相当于提升了这么多倍）。

但问题是用户的请求究竟由哪个节点来处理呢？最好能够让此时此刻负载较小的节点来处理，这样使得每个节点的压力都比较平均。要实现这个功能，就需要在所有节点之前增加一个“调度者”的角色，用户的所有请求都先交给它，然后它根据当前所有节点的负载情况，决定将这个请求交给哪个节点处理。这个“调度者”有个牛逼了名字——==负载均衡服务器==。

集群结构的好处就是系统扩展非常容易。如果随着你们系统业务的发展，当前的系统又支撑不住了，那么给这个集群再增加节点就行了。但是，当你的业务发展到一定程度的时候，你会发现一个问题——无论怎么增加节点，貌似整个集群性能的提升效果并不明显了。这时候，你就需要使用微服务结构了。

##### 分布式结构

先来对前面的知识点做个总结。

从单机结构到集群结构，你的代码基本无需要作任何修改，你要做的仅仅是==多部署几台服务器==，每台服务器上运行相同的代码就行了。但是，当你要从集群结构演进到微服务结构的时候，之前的那套代码就需要发生较大的改动了。所以对于新系统我们建议，系统设计之初就采用微服务架构，这样后期运维的成本更低。但如果一套老系统需要升级成微服务结构的话，那就得对代码大动干戈了。所以，对于老系统而言，究竟是继续保持集群模式，还是升级成微服务架构，这需要你们的架构师深思熟虑、权衡投入产出比。

OK，下面开始介绍所谓的分布式结构。

分布式结构就是将一个完整的系统，按照业务功能，拆分成一个个独立的子系统，在分布式结构中，每个子系统就被称为“服务”。这些子系统能够独立运行在web容器中，它们之间通过RPC方式通信。

举个例子，假设需要开发一个在线商城。按照微服务的思想，我们需要按照功能模块拆分成多个独立的服务，如：用户服务、产品服务、订单服务、后台管理服务、数据分析服务等等。这一个个服务都是一个个独立的项目，可以独立运行。如果服务之间有依赖关系，那么通过RPC方式调用。

这样的好处有很多：

1. 系统之间的耦合度大大降低，可以独立开发、独立部署、独立测试，系统与系统之间的边界非常明确，排错也变得相当容易，开发效率大大提升。
2. 系统之间的耦合度降低，从而系统更易于扩展。我们可以针对性地扩展某些服务。假设这个商城要搞一次大促，下单量可能会大大提升，因此我们可以针对性地提升订单系统、产品系统的节点数量，而对于后台管理系统、数据分析系统而言，节点数量维持原有水平即可。
3. 服务的复用性更高。比如，当我们将用户系统作为单独的服务后，该公司所有的产品都可以使用该系统作为用户系统，无需重复开发。

#### 2. 什么是集群

Redis 集群实现了对Redis的水平扩容，即==启动N个redis节点==，将整个数据库分布存储在这N个节点中，每个节点存储总数据的1/N。

Redis 集群通过分区（partition）来提供一定程度的可用性（==availability==）： 即使集群中有<u>一部分节点失效或者无法进行通讯， 集群也可以继续处理命令请求</u>

#### 3. 集群环境搭建

![image-20200408162309523](pic/image-20200408162309523.png)



# Git & GitHub

![image-20200330184830055](pic/image-20200330184830055.png)

### 1. Git

#### 1. 工作区,本地库(Repository)和暂存区

![image-20200330195118832](pic/image-20200330195118832.png)

##### 1. 创建版本库

在项目文件夹内，执行:  

```
git  init
```

##### 2. 提交文件

新建文件后，通过

```shell
git  status  #进行查看文件状态
git  add [ 文件名] #将文件添加到暂存区
git  commit #提交文件到本地库
编写注释 ，完成提交
git  commit  –m “注释内容”# 直接带注释提交
```

##### 3. 查看文件提交记录

```shell
git  log  [文件名]     #进行查看历史记录
git log  --pretty=oneline [文件名]      #简易信息查看
```

##### 4.回退历史

```shell
git  reset  --hard HEAD^   #回退到上一次提交
git  reset  --hard HEAD~n  #回退n次操作
```

##### 5. 版本穿越

```shell
git  reflog  [文件名]   #查看历史记录的版本号
git  reset  --hard  版本号  #回退n次操作
```

#####6. 还原文件

```shell
git  checkout -- [文件名]   #还原文件
```

##### 7. 删除某个文件

先删除文件
再git add 再提交

#### 2. 分支

![image-20200330200334935](pic/image-20200330200334935.png)

##### 创建分支

```shell
git  branch  <分支名> # 创建分支
git branch –v   #查看分支
```

#####切换分支

```shell
git checkout  <分支名>
git checkout  –b  <分支名> #创建并切换分支
```

#####合并分支

```shell
git  checkout  master #先切换到主干   
git  merge  <分支名>
```

**冲突：**

![image-20200330210854523](pic/image-20200330210854523.png)

![image-20200330210920372](pic/image-20200330210920372.png)

### 2. GitHub

![image-20200330211417710](pic/image-20200330211417710.png)

![image-20200330211451653](pic/image-20200330211451653.png)

##### 1. 增加远程地址

```shell
git remote add  <远端代号>   <远端地址> 
git  remote  add  origin  https://github.com/user111/Helloworld.git
```

> <==远端代号==> 是指远程链接的代号，一般直接用origin作代号，也可以自定义。
> <==远端地址==> 默认远程链接的url

##### 2. 增加远程地址推送到远程库

```shell
git  push   <远端代号>    <本地分支名称>
git  push  origin  master
```

>  <分支名称>  是指要提交的分支名字，比如master。

##### 3. 从GitHub上克隆一个项目

```shell
git  clone   <远端地址>   <新项目目录名>

#命令执行完后，会自动为这个远端地址建一个名为origin的代号
git  clone  https://github.com/user111/Helloworld.git   hello_world 
```

> <项目目录名>  是指为克隆的项目在本地新建的目录名称，可以不填，默认是GitHub的项目名

##### 4. 从GitHub更新项目

```shell
git  pull   <远端代号>   <远端分支名>
git pull origin  master
```

![image-20200330213849832](pic/image-20200330213849832.png)

![image-20200330213934657](pic/image-20200330213934657.png)

![image-20200330213945329](pic/image-20200330213945329.png)

![image-20200330214500571](pic/image-20200330214500571.png)

### 3. 在idea中使用Git

### 4. 分支

#### Git开发流程

简单来说就是，一个项目的成员们在工作中统一使用Git的工作方式

![image-20200330221926737](pic/image-20200330221926737.png)

![image-20200330221935950](pic/image-20200330221935950.png)

![image-20200330221947709](pic/image-20200330221947709.png)

#### 分支种类

- 主干分支 master
      主要负责管理正在运行的生产环境代码。永远保持与正在运行的生产环境完全一致。

- 开发分支   develop
      主要负责管理正在开发过程中的代码。一般情况下应该是最新的代码

- bug修理分支  ==hotfix==
      主要负责管理生产环境下出现的紧急修复的代码。 从主干分支分出，修理完毕并测试上线后，并回主干分支。并回后，视情况可以删除该分支

- 发布版本分支  release
      较大的版本上线前，会从开发分支中分出发布版本分支，进行最后阶段的集成测试。该版本上线后，会合并到主干分支。生产环境运行一段阶段较稳定后可以视情况删除

- 功能分支    feature
      为了不影响较短周期的开发工作，一般把中长期开发模块，会从开发分支中独立出来。 开发完成后会合并到开发分支。

  ![image-20200330222133828](pic/image-20200330222133828.png)

  

### GitLab —“自架私服版”的GitHub





##### 1. 增加远程地址

```shell
git remote add  <远端代号>   <远端地址> 
```

##### 1. 增加远程地址

```shell
git remote add  <远端代号>   <远端地址> 
```

##### 1. 增加远程地址

```shell
git remote add  <远端代号>   <远端地址> 
```

# Shell

**什么是SHELL？**

​	    [Shell](https://www.baidu.com/s?wd=Shell&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)俗称壳（用来区别于内核），是指“提供使用者使用界面”的软件，就是一个==命令行解释器==。

**SHELL的版本**
　　早在UNIX年代，发展者众多，所以由于shell依据发展者的不同就有许多版本，比如sh,C SHell,K SHell,还有TCSH等，每一种Shell都各有特点。当然也有我们的bash,bash这个shell是Bourne  Shell的增强版本，也是基于GNU的架构下发展出来的。

**sh和bash的区别**
　　bash是sh的增强版本。bash 是一个为[GNU](https://www.baidu.com/s?wd=GNU&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)项目编写的Unix [shell](https://www.baidu.com/s?wd=shell&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)，也就是[linux](https://www.baidu.com/s?wd=linux&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)用的[shell](https://www.baidu.com/s?wd=shell&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)。



```mermaid
graph TD
			subgraph 外部应用程序
			subgraph Shell
			subgraph Linux内核
			硬件
			end
			end
			end
```

查看shell版本：

```shell
cxy@Cxy:~$ cat /etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/bash
/bin/rbash
/bin/dash
```

### Shell 脚本

Shell 脚本（shell script），是一种为 shell 编写的脚本程序。业界所说的 shell 通常都是指 shell 脚本，但读者朋友要知道，shell 和 shell script 是两个不同的概念。简单的说**shell脚本可以放平时我们操作终端的命令**

### 1．Shell脚本入门

脚本以

```shell
# !/bin/bash
```

开头，意在指定解析器

#### 第一个Shell脚本：helloworld

1. 创建脚本

```sh
vim [文件名].sh
```

2. 写脚本

```shell
#!/bin/bash
echo "helloworld"
```

####  脚本的常用执行方式

1. 采用bash或sh+脚本的相对路径或绝对路径（不用赋予脚本+x权限）

```shell
$ sh helloworld.sh 
$ bash helloworld.sh 
```

2. 采用输入脚本的绝对路径或相对路径执行脚本（必须具有可执行权限+x）

   ```shell
   chmod 777 helloworld.sh
    ./helloworld.sh 
   ```

==注意==：第一种执行方法，本质是bash解析器帮你执行脚本，所以脚本本身不需要执行权限。第二种执行方法，本质是脚本需要自己执行，所以需要执行权限。

#### 第二个Shell脚本：多命令处理

```shell
$ touch batch.sh
$ vi batch.sh

#在batch.sh中输入如下内容

\#!/bin/bash

cd /home/atguigu
touch cls.txt
echo "I love cls" >>cls.txt
```

### 2. Shell中的变量

#### 1.系统变量

常用系统变量

`$HOME、$PWD、$SHELL、$USER等`

```shell
#查看系统变量的值
echo $HOME

#显示当前Shell中所有变量
set
```

#### 2 自定义变量

1．基本语法

（1）定义变量：变量=值

（2）撤销变量：==unset== 变量

（3）声明静态变量：readonly变量，注意：不能unset

2．变量定义规则

​	（1）变量名称可以由字母、数字和下划线组成，但是不能以数字开头，环境变量名建议大写。

​	（2==）等号两侧不能有空格==

​	（3）在bash中，==变量默认类型都是字符串类型==，无法直接进行数值运算。

​	（4）变量的值如果有空格，需要使用双引号或单引号括起来。

3．案例实操

```shell
A=5
echo $A

unset A
echo $A

D="I love banzhang"
```

#### 3.特殊变量

##### $n

1．基本语法

​	`$n`	:   n为数字

- `$0`代表该脚本名称
- `$1-$9`代表第1到第9个参数，10以上的参数，10以上的参数需要用大括号包含，如${10}

```shell
$ vim parameter.sh

#输入：
\#!/bin/bash

echo "$0  $1   $2"

$ bash parameter.sh cls  xz
```

##### $#

```
$# ：获取所有输入参数个数，常用于循环
```

```shell
$ vim parameter.sh

#输入：
\#!/bin/bash

echo "$#"

$ bash parameter.sh cls  xz cl
```

##### `$*、$@`

```
$* ：代表命令行中所有的参数，把所有的参数看成一个整体 
@* : 代表命令行中所有的参数，	把每个参数区分对待
```

```shell
$ vim parameter.sh

#输入：
\#!/bin/bash

\#!/bin/bash

echo "$0  $1   $2"
echo $#
echo $*
echo $@

cxy@Cxy:~$ bash t.sh 1 2 3
t.sh  1   2
3
1 2 3
1 2 3
```

##### $？

1．基本语法

$？ ：最后一次执行的命令的返回状态。

> 如果这个变量的值为0，证明上一个命令正确执行
>
> 如果这个变量的值为非0，则证明上一个命令执行不正确了

### 3. 运算符

- `$((运算式))`
- `$[运算式]`
- expr + , - , \*,  /,  %    加，减，乘，除，取余

注意：==expr运算符间要有空格==

```shell
S=$(((2+3)*4))
#20

S=$[(2+3)*4]
#20

$ expr 2 + 3
5

expr `expr 2 + 3` \* 4
20
```

###4. 条件判断

```
[ condition ]
```

注意：

- condition前后要有空格
- 条件非空即为true，[ atguigu ]返回true，[] 返回false。



常用判断条件

- 两个整数之间比较

  > | -lt 小于（less than）						-le 小于等于（less equal） |      |
  > | ------------------------------------------------------------ | ---- |
  > | -eq 等于（equal）							-gt 大于（greater than） |      |
  > | -ge 大于等于（greater equal）	-ne 不等于（Not equal）     |      |

- 按照文件==权限==进行判断

  > - -r 有读的权限（read）	
  > - -w 有写的权限（write）
  > - -x 有执行的权限（execute）

- 按照文件==类型==进行判断

  > - -f 文件存在并且是一个常规的文件（file）
  > - -e 文件存在（existence）		
  > - -d 文件存在并是一个目录（directory）

```shell
$ [ 23 -ge 22 ]
$ echo $?
0

$ [ -w helloworld.sh ]
$ echo $?
0

$ [ -e /home/atguigu/cls.txt ]
$ echo $?
```

- 多条件判断（&& 表示前一条命令执行成功时，才执行后一条命令，|| 表示上一条命令执行失败后，才执行下一条命令）

  ```shell
  $ [ condition ] && echo OK || echo notok
  OK
  
  $ [ condition ] && [ ] || echo notok
  notok
  ```

### 5. 流程控制（重点）

#### if 判断

```shell
if [ 条件判断式 ];then 
  程序 
fi

#或者 

if [ 条件判断式 ]
then
					程序 
					elif [ 条件判断式 ]
					then
										程序
					else
										程序
fi 
```

（1）[ 条件判断式 ]，中括号和条件判断式之间必须有空格

（2）==if后要有空格==

```shell
#!/bin/bash
if [ $1 -eq "1" ]
then
        echo "banzhang zhen shuai"
elif [ $1 -eq "2" ]
then
				echo "cls zhen mei"
fi
```

#### case 语句

```shell
case $变量名 in 
  "值1"）
		如果变量的值等于值1，则执行程序1
		;; 

  "值2"）
	  如果变量的值等于值2，则执行程序2
	   ;; 
	   
	   …省略其他分支… 
  *）

		如果变量的值都不是以上的值，则执行此程序 
	  ;; 
esac
```

注意事项：

1. case行尾必须为单词“in”，每一个模式匹配必须以右括号“）”结束。
2. 双分号“**;;**”表示命令序列结束，相当于java中的break。
3. 最后的“==*）==”表示默认模式，相当于java中的default。

```shell
#!/bin/bash

case $1 in
"1")
		 echo "banzhang"
;;

"2")
			echo "cls"
;;

*)
			echo "renyao"
;;
esac
```

#### for 循环

1. 基本for循环

```shell
for (( 初始值;循环控制条件;变量变化 )) 
do 
  			程序 
done
```

```shell
\#!/bin/bash
s=0
for((i=0;i<=100;i++))
do
			s=$[$s+$i]
done
echo $s
```

2. foreach循环

```shell
for 变量 in 值1 值2 值3…
do 
			 程序 
done
```

```shell
#!/bin/bash
for i in $*
do 
			 echo "ban zhang love $i "
done
```

**比较`$*`和`$@`区别**

（a）$*和$@都表示传递给函数或脚本的所有参数，不被双引号“”包含时，都以`$1 $2 …$n`的形式输出所有参数。

（b）当它们被双引号“”包含时，`"$*"`会将所有的参数作为一个整体，以`$1, $2 ,…$n`的形式输出所有参数；`"$@"`会将各个参数分开，以“$1” “$2”…”$n”的形式输出所有参数。

```shell
\#!/bin/bash
for i in "$*"
\#$*中的所有参数看成是一个整体，所以这个for循环只会循环一次
do
			echo "ban zhang love $i"
done

for j in "$@"
\#$@中的每个参数都看成是独立的，所以“$@”中有几个参数，就会循环几次
do
			echo "ban zhang love $j" 
done
```









[atguigu@hadoop101 datas]$ chmod 777 for.sh

[atguigu@hadoop101 datas]$ bash for.sh cls xz bd

ban zhang love cls xz bd

ban zhang love cls

ban zhang love xz

ban zhang love bd

####while 循环

```shell
while [ 条件判断式 ] 
do 
			程序
done
```

```shell
#!/bin/bash
s=0
i=1
while [ $i -le 100 ]
do
			 s=$[$s+$i]
       i=$[$i+1]
done
echo $s
```

### 6. read读取控制台输入

```
read(选项)(参数)
```

> 选项：
>
> - -p：指定读取值时的提示符
> - -t：指定读取值时等待的时间（秒
>
> 参数：
>
> - 变量：指定读取值的变量名

```shell
#!/bin/bash

read -t 7 -p "Enter your name in 7 seconds " NAME
echo $NAME
```



### 7. 函数

#### 系统函数

1．==basename==基本语法

```shell
basename [string / pathname] [suffix]  ：basename命令会删掉所有的前缀包括最后一个（‘/’）字符，然后将字符串显示出来
```

> suffix为后缀，如果suffix被指定了，basename会将pathname或string中的suffix去掉。

```shell
$ basename /home/atguigu/banzhang.txt 
banzhang.txt

$ basename /home/atguigu/banzhang.txt .txt
banzhang
```



2. ==dirname==基本语法

```shell
dirname 文件绝对路径 ：从给定的包含绝对路径的文件名中去除文件名（非目录的部分），然后返回剩下的路径（目录的部分）
```

> ```shell
> $ dirname /home/atguigu/banzhang.txt 
> /home/atguigu
> ```

####自定义函数

1．基本语法

```shell
[ function ] funname[()]
{
			Action;
      [return int;]

}

funname
```



2．经验技巧

​	（1）必须在调用函数地方之前，先声明函数，==shell脚本是逐行运行==。不会像其它语言一样先编译。

​	（2）函数返回值，==只能通过$?系统变量获得==，可以显示加：return返回，如果不加，将以最后一条命令运行结果，作为返回值。return后跟数值 n(0-255)。==返回值代表是否成功==

3．案例实操

​	（1）计算两个输入参数的和

```shell
#!/bin/bash
function sum()
{
     s=0
     s=$[ $1 + $2 ]
     echo "$s"
}

read -p "Please input the number1: " n1;
read -p "Please input the number2: " n2;
sum $n1 $n2;
```

###8. Shell工具（重点）

#### 1. cut

cut的工作就是“剪”，具体的说就是在文件中负责==剪切数据==用的。cut 命令从文件的每一行剪切字节、字符和字段并将这些字节、字符和字段输出。

1. 基本用法

```shell
cut [选项参数] filename
```

> 说明：默认分隔符是制表符

2.选项参数说明

> | 选项参数 | 功能                         |
> | -------- | ---------------------------- |
> | -f       | 列号，提取第几列             |
> | -d       | 分隔符，按照指定分隔符分割列 |
> | -c       | 指定具体的字符               |



3.案例实操

```shell
数据：
dong shen
guan zhen
wo  wo
lai  lai
le  le

# 切割cut.txt第一列
$ cut -d " " -f 1 cut.txt 

#切割cut.txt第二、三列
[atguigu@hadoop101 datas]$ cut -d " " -f 2,3 cut.txt 

#在cut.txt文件中切割出guan
$ cat cut.txt | grep "guan" | cut -d " " -f 1
```

```shell
$ echo $PATH
/usr/lib64/qt-3.3/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/atguigu/bin
#选取系统PATH变量值，第2个“：”开始后的所有路径：
$ echo $PATH | cut -d : -f 2-

#切割ifconfig 后打印的IP地址
$ ifconfig eth0 | grep "inet addr" | cut -d : -f 2 | cut -d" " -f1
192.168.1.102
```

#### 2. sed

sed是一种==流编辑器==，它一次处理一行内容。处理时，把==当前处理的行==存储在临时缓冲区中，称为“模式空间”，接着用sed命令处理缓冲区中的内容，处理完成后，把缓冲区的内容送往屏幕。接着处理下一行，这样不断重复，直到文件末尾。文件内容并没有改变，除非你使用重定向存储输出。

1. 基本用法

```shell
sed [选项参数] ‘command’  filename
```

2. 选项参数说明

3. 

> | 选项参数 | 功能                         |
> | -------- | ---------------------------- |
> | -f       | 列号，提取第几列             |
> | -d       | 分隔符，按照指定分隔符分割列 |
> | -c       | 指定具体的字符               |

3. 命令功能描述

4. 

> | 命令 | 功能                                      |
> | ---- | ----------------------------------------- |
> | a    | ==新增==，a的后面可以接字串，在下一行出现 |
> | d    | ==删除==                                  |
> | s    | ==查找并替换==                            |



##### 正则匹配

```
\   转义
^   一行的开头
    ^R------表示以R开头的行
$   匹配一行的结束
    R$表示以R结尾的行

*   表示上一个子式匹配0次或多次，贪心匹配
    Zo*-----
            Z
            Zo
            Zooo
    .   匹配一个任意的字符
    .*匹配任意字符串
    []  表示匹配某个范围内的字符
    [a-z]------匹配一个a-z之间的字符
    [a-z]*-----匹配任意字母字符串
```

4. 案例实操

```shell
数据：
dong shen
guan zhen
wo  wo
lai  lai
le  le
```

```shell
#将“mei nv”这个单词插入到sed.txt第二行下，打印。
$ sed '2a mei nv' sed.txt 
```

>  注意：==文件并没有改变==

```shell
#删除sed.txt文件所有包含wo的行
$ sed '/wo/d' sed.txt
```

>  注意：‘==g’表示global==，全部替换

```shell
#将sed.txt文件中wo替换为ni
$ sed 's/wo/ni/g' sed.txt 
```

####3. awk

一个强大的文本分析工具，把文件逐行的读入，以空格为默认分隔符将==每行切片，切开的部分再进行分析处理==。

1. 基本用法

```shell
awk [选项参数] 'pattern1{action1}  pattern2{action2}...' filename

pattern：表示AWK在数据中查找的内容，就是匹配模式

action：在找到匹配内容时所执行的一系列命令
```

1. 注意：

2. - 只有==匹配了pattern的行才会执行action==
   - 正则表达式用//包起来

3. 

4. 选项参数说明

> | 选项参数 | 功能                 |
> | -------- | -------------------- |
> | -F       | 指定输入文件折分隔符 |
> | -v       | 赋值一个用户定义变量 |



3. 案例实操

4. ==这里的 \$ n 表示第几列==

```shell
#数据准备
$ sudo cp /etc/passwd ./

#搜索passwd文件以root关键字开头的所有行，并输出该行的第7列。
[atguigu@hadoop102 datas]$ awk -F : '/^root/{print $7}' passwd
/bin/bash

#搜索passwd文件以root关键字开头的所有行，并输出该行的第1列和第7列，中间以“，”号分割。
$ awk -F : '/^root/{print $1","$7}' passwd 
root,/bin/bash
```

```shell
#只显示/etc/passwd的第一列和第七列，以逗号分割，且在所有行前面添加列名user，shell ，在最后一行添加"dahaige，/bin/zuishuai"。
$ awk -F : 'BEGIN{print "user, shell"} {print $1","$7} END{print "dahaige,/bin/zuishuai"}' passwd
```

> 注意：==BEGIN== 在所有数据读取行之前执行；==END==在所有数据执行之后执行

```shell
#将passwd文件中的用户id增加数值1并输出
$ awk -v i=1 -F: '{print $3+i}' passwd
```

4. awk的内置变量

5. 

> | 选项参数 | 说明                                   |
> | -------- | -------------------------------------- |
> | FILENAME | 文件名                                 |
> | NR       | 已读的记录数(行)                       |
> | NF       | 浏览记录的域的个数（切割后，列的个数） |



5. 案例实操

```shell
#统计passwd文件名，每行的行号，每行的列数
$ awk -F: '{print "filename:"  FILENAME ", linenumber:" NR  ",columns:" NF}' passwd 

#切割IP
$ ifconfig eth0 | grep "inet addr" | awk -F: '{print $2}' | awk -F " " '{print $1}' 

#查询sed.txt中空行所在的行号
$ awk '/^$/{print NR}' sed.txt 
```



#### 4. sort

sort命令是在Linux里非常有用，它将文件进行排序，并将排序结果标准输出。

1. 基本语法

   ```
   sort(选项)(参数)
   ```

   

> | 选项 | 功能                     |
> | ---- | ------------------------ |
> | -n   | 依照数值的大小排序       |
> | -r   | 以相反的顺序来排序       |
> | -t   | 设置排序时所用的分隔字符 |
> | -k   | 指定需要排序的列         |

>  **参数**：指定待排序的文件列表



```shell
$ cat passwd | grep ^a | sort -t : -k 3 -n
```





# 面试题

## Java 基础

### 1.包装类

```java
Object o1 = true ? new Integer(1) : new Double(2.0);
System.out.println(o1);// 1.0，自动类型提升

Object o2;
if (true)
	o2 = new Integer(1);
else
	o2 = new Double(2.0);
System.out.println(o2);// 1

//Integer内部定义了IntegerCache结构，IntegerCache中定义了Integer[],
//保存了从-128~127范围的整数。如果我们使用自动装箱的方式，给Integer赋值的范围在
//-128~127范围内时，可以直接使用数组中的元素，不用再去new了。目的：提高效率
Integer m = 1;
Integer n = 1;
System.out.println(m == n);//true

Integer x = 128;//相当于new了一个Integer对象
Integer y = 128;//相当于new了一个Integer对象
System.out.println(x == y);//false
```



### 2. 面向对象



## Java 高级

### 多线程

#### 1 synchronized 与 Lock的异同？

- 相同：二者都可以解决线程安全问题

- 不同：synchronized机制在执行完相应的同步代码以后，==自动==的释放同步监视器,

  ​	    Lock需要==手动==的启动同步（lock()），同时结束同步也需要手动的实现（unlock()）

#### 2 sleep() 和 wait()的异同？

- 相同：一旦执行方法，都可以使得当前的线程进入<u>阻塞</u>状态。
- 不同：
- - 1. 两个方法声明的位置不同：Thread类中声明sleep() , Object类中声明wait()
    2. 调用的要求不同：sleep()可以在任何需要的场景下调用。 wait()必须使用在同步代码块或同步方法中
    3. 关于是否释放同步监视器：如果两个方法都使用在同步代码块或同步方法中，sleep()不会释放锁，wait()会==释放锁== 。

#### 3 创建多线程有几种方式？

四种！

### 常用类

#### 1. String

```java
//通过字面量定义的方式：此时的s1和s2的数据javaEE声明在方法区中的字符串常量池中。
String s1 = "javaEE";
String s2 = "javaEE";
//通过new + 构造器的方式:此时的s3和s4保存的地址值，是数据在堆空间中开辟空间以后对应的地址值。
String s3 = new String("javaEE");
String s4 = new String("javaEE");
System.out.println(s1 == s2);//true
System.out.println(s1 == s3);//false
System.out.println(s1 == s4);//false
System.out.println(s3 == s4);//false
```

```mermaid
graph LR
	subgraph 栈
	s1:0x1212
	s2:0x1212
	s3:0x8899
	s4:0x7777
	end
	s1:0x1212 --> JavaEE
	s2:0x1212 --> JavaEE
	s3:0x8899 --> 0x8899:values
	s4:0x7777 --> 0x7777:values
	subgraph 字符串常量池
	JavaEE
	end
	subgraph 堆
	0x8899:values
	0x7777:values
	end
	
	0x8899:values --> JavaEE
	0x7777:values --> JavaEE
```

- String s = new String("abc");方式创建对象，在内存中创建了几个对象？

  两个:一个是堆空间中new结构，另一个是char[]对应的常量池中的数据："abc"(假设常量池中原来没有abc)

### 集合

#### 1. ArrayList、LinkedList、Vector三者的异同？

*  同：三个类都是实现了List接口，存储数据的特点相同：存储有序的、可重复的数据

*  不同：

*  - 1. ArrayList：作为List接口的主要实现类；线程不安全的，效率高；底层使用Object[] elementData存储
     2. LinkedList：对于频繁的插入、删除操作，使用此类效率比ArrayList高；底层使用双向链表存储
     3. Vector：作为List接口的古老实现类；线程安全的，效率低；底层使用Object[] elementData存储

#### 2. Map

- 1. HashMap的底层实现原理？
  2. HashMap 和 Hashtable的异同？
  3. CurrentHashMap 与 Hashtable的异同？（暂时不讲）

#### 3. Collection和Collections的区别 



## MySQL

### 事务

#### 1.  事务的特点、特性？

ACID：

1. 原子性

   事务的sql语句的划分，必须小到不能在小。 这一组操作是否真的要求：要么同时成功，要么同时失败。

2. 一致性

   保证事务前后数据一致性 。

   例如：张三原来余额：500，李四原来余额：2000，张三要给李四转 500 

   > 一致性：事务之前  张三原来余额：500，李四原来余额：2000。
   >
   > 事务之后：
   >
   > > 如果失败，张三余额：500，李四原来余额：2000
   > > 如果成功，张三余额：0，李四原来余额：2500

3. 隔离性

   两个事务之间是独立。
   例如：张三给李四转500，李四给王五转1000，赵六给李四转800，

   ​            这三个事务是独立的，张三给李四转账的成功与失败与  其他两个操作无关。

4. 持久性：一旦提交就确定了。

mysql中只有 ==Innodb 引擎== 才支持事务。事务只对DML语句有效，对DDL语句无效。

## Shell

####京东

1. 使用Linux命令查询file1中空行所在的行号

```shell
$ awk /^$/{print NR} file1.txt
```

2. 有文件chengji.txt内容如下:

张三 40

李四 50

王五 60

使用Linux命令计算第二列的和并输出

```shell
cat chengji.txt | awk -F " " '{sum+=$2} END{print sum}'
#or
awk -F " " '{sum+=$2} END{print sum}' chengji.txt
```



####搜狐&和讯网

1. Shell脚本里如何检查一个文件是否存在？如果不存在该如何处理？

```shell
#!/bin/bash
if [ -f file.txt ]; then
   echo "文件存在!"
else
   echo "文件不存在!"
fi
```



#### 新浪

1. 用shell写一个脚本，对文本中无序的一列数字排序,并求和

```shell
$cat test.txt
9
8
7
6
5
4
3
2
10
1
$sort -n test.txt | awk '{a+=$0;print $0}END{print "SUM="a}'
```



####金和网络

1.请用shell脚本写出查找当前文件夹（/home）下所有的文本文件内容中包含有字符”shen”的文件名称

```shell
$ awk 
$ grep -r "shen" /home |cut -d ":" -f 1
# -r表示递归操作 ，grep -r "shen" /home表示对/home目录进行递归操作，找出所有包含"shen"的路径
```

