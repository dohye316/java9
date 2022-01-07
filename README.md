# java9

面向对象三大特征
封装 继承 多态

封装：encapsulaion 就是把抽象出的数据（属性）和对数据的操作（方法）封装在一起，数据被保护在内部，程序的其他部分只有通过被授权的操作【方法】，才能对数据进行操作

封装的理解和好处
1.隐藏实现细节 方法 (链接数据库)<---调用（传入参数）
2.可以对数据进行验证，保证安全合理
Person{name,age}

封装的实现步骤(三步)
1.将属性进行私有化private【不能直接修改属性】
2.提供一个公共的（public）set方法，用于对属性判断并赋值
public void setXxx（类型 参数名）{
//加入数据验证的业务逻辑
属性= 参数名；
}
3.提供一个公共的（public）get方法，用于获取属性的值
public 数据类型 getXxx（）{//权限判断
  return xx;}
===============================================================
看一个案例
name在java中如何实现这种类似的控制呢？
请大家看一个小程序（Encap01.java）,不能随便查看人的年龄，工资的等隐私，并对设置的年龄进行合理的验证。年龄合理就设置，否则给默认年龄必须在1-120，年龄，工资不能直接查看，name的长度在2-6之间
com.hspedu.encap

package com.hspedu.encapsulate;



public class Encapsulation01 {
    public static void main(String[] args) {


//    name在java中如何实现这种类似的控制呢？
//    请大家看一个小程序（Encap01.java）,不能随便查
//    看人的年龄，工资的等隐私，并对设置的年龄进行合
//    理的验证。年龄合理就设置，否则给默认年龄必须在1
//    -120，年龄，工资不能直接查看，name的长度在2-
//    6之间
//    com.hspedu.encap
        Person person = new Person();
        //如果要使用快捷键 alt r 先配置一下主类
        //第一次，我们使用鼠标电极形式运算程序，后面就可以用
        person.setName("jack[;;p;p");
        person.setAge(300);
        person.setSalary(30000);
        System.out.println(person.info());
        System.out.println(person.getSalary());

    }
}
class Person{
    public String name;//名字公开
    private int age;//年龄私有化
    private double salary;//薪资
    //自己写太慢 alt + ins
    //然后根据要求俩完善我们的代码


    public String getName() {
        return name;
    }

    public void setName(String name) {
        //加入对数据的校验
        if (name.length() > 2 && name.length() <= 6) {
            this.name = name;
        }else{
            System.out.println("名字的长度不对,需要（2-6）");
            this.name ="无名人";
        }

    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        if (age >= 1&& age <= 120 ) {
            this.age = age;
        }else{
            System.out.println("你设置的年龄不对，年龄需要在1-120");
            this.age = 18;//给一个默认年龄
        }
    }

    public double getSalary() {
        //可以这里增加对当前对象的权限判断
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }
    public String info(){
        return"信息为 name=" + name + "\tage=" + age + "薪水" + salary;
    }
}//写一个方法，返回属性信息

private   不让别的包里的人控制属性



================================================================






可以添加 Person 构造器的方法  用setName 改造信息
package com.hspedu.encapsulate;



public class Encapsulation01 {
    public static void main(String[] args) {


//    name在java中如何实现这种类似的控制呢？
//    请大家看一个小程序（Encap01.java）,不能随便查
//    看人的年龄，工资的等隐私，并对设置的年龄进行合
//    理的验证。年龄合理就设置，否则给默认年龄必须在1
//    -120，年龄，工资不能直接查看，name的长度在2-
//    6之间
//    com.hspedu.encap


        //如果要使用快捷键 alt r 先配置一下主类
        //第一次，我们使用鼠标电极形式运算程序，后面就可以用
        Person person = new Person();
        
        person.setName("jack");
        person.setAge(300);
        person.setSalary(30000);
        System.out.println(person.info());
        System.out.println(person.getSalary());
        //如果我们自己使用构造器指定属性
        Person smith = new Person("smith", 2000, 5000000);
        System.out.println("=====simth的信息=====");
        System.out.println(smith.info());


    }
}
class Person{
    public String name;//名字公开
    private int age;//年龄私有化
    private double salary;//薪资
    //自己写太慢 alt + ins
    //然后根据要求俩完善我们的代码
  


    //有三个属性的构造器
    public Person(String name, int age, double salary){
//        this.name = name;
//        this.age =age;
//        this.salary = salary;
        //我们可以将set方法写在构造器中，这杨仍然可以验证
        setName(name);
        setAge(age);
        setSalary(salary);
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        //加入对数据的校验
        if (name.length() > 2 && name.length() <= 6) {
            this.name = name;
        }else{
            System.out.println("名字的长度不对,需要（2-6）");
            this.name ="无名人";
        }

    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        if (age >= 1&& age <= 120 ) {
            this.age = age;
        }else{
            System.out.println("你设置的年龄不对，年龄需要在1-120");
            this.age = 18;//给一个默认年龄
        }
    }

    public double getSalary() {
        //可以这里增加对当前对象的权限判断
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }
    public String info(){
        return"信息为 name=" + name + "\tage=" + age + "薪水" + salary;
    }
}//写一个方法，返回属性信息

 面向对象编程 封装
创建程序，在其中定义两个类：Account和AccountTest类体会java的封装性。
1.Account类要求具有属性：姓名（长度为2位3位或4位），余额（必须>20）,密码（必须是六位），如果不满足，则给出提示信息，并给默认值
2.通过setXxx的方法给Account的属性赋值
3.在AccountTest中测试
提示只是点
String name = ""
int len = name.lenth();

=======================================================
package com.hspedu.encapsulate;

class Acount {
    private String name = " ";
    private double balance;
    private String passworld;
    //提供两个构造器


    public Acount(){

    }
    public Acount(String name, double balance, String passworld){
        this.setName(name);
        this.setBalance(balance);
        this.setPassworld(passworld);

    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        if (name.length() >= 2 && name.length() <= 4) {
            this.name = name;
        } else {
            System.out.println("输入错误请输入2位3位4位的名字");
        }

    }

    public double getBalance() {
        return  balance;
    }

    public void setBalance(double balance) {
        if (balance >= 20) {
            this.balance = balance;
        } else {
            System.out.println("输入错误余额必须>0默认为0");
        }

    }

    public String getPassworld() {
        return passworld;
    }

    public void setPassworld(String passworld) {
        int len = passworld.length();
        if (len == 6) {

            this.passworld = passworld;
        }else{ System.out.println("默认为六个0");
            this.passworld = "000000";
        }

    }public void info(){
        //增加一个权限的校验
        if (name == "jack") {


            System.out.println("name=" + name + "money=" + balance + "passworld"+ passworld);
        }else{
            System.out.println("你无权");
        }
    }
}

package com.hspedu.encapsulate;

class AccountTest {
    public static void main(String[] args) {


        Acount acount = new Acount();
        acount.setName("jack");
        acount.setBalance(500);
        acount.setPassworld("123456");
        acount.info();
name=jackmoney=500.0passworld123456  

    }

}
当名字不是jack 的时候无法访问这就是封装




用
=========================================================



继承extends
为什么需要继承  com.hspedu.extend_包：Extends01.java
一个小问题，还是看个程序提出代码复用的问题
我们编写了两个类，一个是Pupil类（小学生），一个是Graduate（研究生）.
问题：两个类的属性和方法有很多是相同的，怎么办

面向对象编程 继承
继承可以解决代码复用，让我们的编程更加靠近人类思维，当多个类存在相同的属性（变量）和方法时，可以从这些类中抽象出父类，在父类中定义这些相同的属性和方法，所有的子类不需要重新定义这些属性和方法，只需要通过extends 来声明继承父亲即可
继承的基本语法
class子类extends父类{}
1.子类就会自动拥有父类定义的属性和方法
2.父类又叫超类，基类。
3.子类又叫派生类


快速入门
我们对Extends01.java改进，使用继承的方法，请大家注意体会使用继承的好处

有了继承代码的复用性提高了
代码的扩展性和维护性提高了
继承的深入讨论/细节问题
子类继承了所有的属性和方法，但是私有属性不能再子类直接访问，要通过公共的方法区访问、
private不能被extend继承


继承的深入讨论/细节问题
子类继承了所有的属性和方法，非私有的属性和方法可以再子类直接访问，但是私有属性和方法不能在子类直接访问，要通过公共的方法去访问


子类必须调用父类的构造器，完成父类的初始化
当创建子类对象时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中用super去指定使用父类的哪个构造器完成对父类的初始化工作，否则，编译不会通过


package com.hspedu.encapsulate.extend_.improve;

public class Base {//父类//四个属性
    public int n1 = 100;
    protected int n2 = 200;
    int n3 = 300;
    private int n4 = 400;
    public Base(){//无参构造器
        System.out.println("base()....");

    }public int getN4(){
        return n4;
    }

    public void test100(){//
        System.out.println("test100");
    }protected void test200(){
        System.out.println("test200");
    }void test300(){
        System.out.println("test300");

    }
    public void getTest400(){
        System.out.println("test400");
    }//Ok 父类提供一个public 的方法

}
class Sub extends Base{//子类

    public Sub() {
子类无参构造器下下面隐藏着 super（）；说明继承，默认调用父类的无参构造器当创建子类对象时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中用super去指定使用父类的哪个构造器完成对父类的初始化工作，否则，编译不会通过

        System.out.println("sub()。。。");
    }
    public void sayOk() {
        System.out.println(n1 +" " + n2 + " " + n3 + " "+ getN4() );//输入n4报错因为是私有的
        test100();
        test200();
        test300();
       getTest400();
    }



}
class extend{
    public static void main(String[] args) {
        Sub sub = new Sub();
        sub.getTest400();
        sub.sayOk();
        sub.getTest400();
    }
}

package com.hspedu.encapsulate.extend_.improve;

public class Base {//父类//四个属性

    public int n1 = 100;
    protected int n2 = 200;
    int n3 = 300;
    private int n4 = 400;
//    public Base(){//无参构造器       无参构造器被覆盖或没有   在子类构造器下必须有super（String name，int age等）
//        System.out.println("base()....");
//
//    }

    public Base(String name,int age){
        System.out.println("父亲的...");
    }
    public int getN4(){
        return n4;
    }

    public void test100(){//
        System.out.println("test100");
    }protected void test200(){
        System.out.println("test200");
    }void test300(){
        System.out.println("test300");

    }
    public void getTest400(){
        System.out.println("test400");
    }//Ok 父类提供一个public 的方法

}
class Sub extends Base{//子类

    public Sub() {
//        super();//隐藏着   如果父类没有写无参构造器或被覆盖一定要写super（）
        super("smith",10);
       System.out.println("sub()。。。");
    }
//    public Sub(){
//
//        System.out.println("String类");
//    }
    public void sayOk() {
        System.out.println(n1 +" " + n2 + " " + n3 + " "+ getN4() );//输入n4报错因为是私有的
        test100();
        test200();
        test300();
       getTest400();
    }



}
class extend{
    public static void main(String[] args) {
        Sub sub = new Sub();
        System.out.println("=============");
        Sub sub2 = new Sub();//先调用父亲的在调用自己的


    }
}
4.如果希望指定去调用父类的某个构造器，则显示的调用一下
5.super在使用时，需要放在构造器第一行
6.super（）和this（）都只能放在构造器第一行，因此这两个方法不能共存在一个构造器
package com.hspedu.encapsulate.extend_.improve;
//ctrl + h 可以看到类的继承关系
public class Base {//父类//四个属性

    public int n1 = 100;
    protected int n2 = 200;
    int n3 = 300;
    private int n4 = 400;
    String name;
    int age;
//    public Base(){//无参构造器       无参构造器被覆盖或没有   在子类构造器下必须有super（String name，int age等）
//        System.out.println("base()....");
//
//    }

    public Base(){

        System.out.println("我是Base无参构造器");
    }
    public Base(String name,int age){
        this.name = name;
        this.age = age;
        System.out.println("父亲的 String   int" + name+ age);

    }
    public Base(String name){
        System.out.println("父类的Base（String name）构造器被调用");
    }
    public int getN4(){
        return n4;
    }

    public void test100(){//
        System.out.println("test100");
    }protected void test200(){
        System.out.println("test200");
    }void test300(){
        System.out.println("test300");

    }
    public void getTest400(){
        System.out.println("test400");
    }//Ok 父类提供一个public 的方法

}
class Sub extends Base{//子类
    public Sub(){
      super();
        System.out.println("我是儿子无参");
    }


    public Sub(String name,int age){
        //1.老师要调用父类的无参构造器，如下或者，什么都不写，默认就是调用super()
     super("jdsjfks",555);;//父类的无参构造器,或者空着
        System.out.println("子类 String  int 被调用");
    }

    public Sub(String name) {
      super("sjskdfj");//隐藏着   如果父类没有写无参构造器或被覆盖一定要写super（）

       System.out.println("sub()String。");
    }
//    public Sub(){
//
//        System.out.println("String类");
//    }
    public void sayOk() {
        System.out.println(n1 +" " + n2 + " " + n3 + " "+ getN4() );//输入n4报错因为是私有的
        test100();
        test200();
        test300();
       getTest400();
    }



}
class extend{
    public static void main(String[] args) {
        System.out.println("=====第一个对象=====");
        Sub sub = new Sub();

        System.out.println("======第2个对象=====");
        Sub sub2 = new Sub("jack",123);
        System.out.println("======第三个对象=====");
        Sub sub3 = new Sub("okkd");

    }
}
=====第一个对象=====
我是Base无参构造器
我是儿子无参
======第2个对象=====
父亲的 String   intjdsjfks555
子类 String  int 被调用
======第三个对象=====
父类的Base（String name）构造器被调用
sub()String。




先写父类构造器 然后写儿子构造器


java所有类都是Object类的子类，Object是所有类的父类

9.子类最多只能继承一个父类，即java中时单继承机制。
10.不能滥用继承，子类和父类之间必须满足 is- a 的逻辑关系
Person is a Music
Person  Music
Music extends Person
Animal
Cat extents Animal
//案例
我们看一个案例来分析当子类继承父类，创建子类对象时，内存中到底发生了什么？ 当子类对象创建好后，建立查找的关系

从子类开始向上找，看有没有此属性
如果子类没有继续找，父类有没有，如果父类有该属性，并且可以访问，就返回信息，直到object，如果都没有会报错
public class ExtendsTheory {
    public static void main(String[] args) {
            Son son = new Son();//内存的布局
        System.out.println(son.name);//返回大头儿子
        System.out.println(son.age);//返回39
        System.out.println(son.hobby);//返回旅游 
        //如果设定private就不能返回
   只能在父类创建public int getXxx（）{
return Xxx}
的方式访问
    }
}
class GrandPa{
    String name ="大头爷爷";
    String hobby = "旅游";

}class Father extends GrandPa{
    String name = "大头爷爷";
    int age = 39;
}
class Son extends  Father{
    String name ="大头儿子";
}



==================
下面答案案是=

public class Test {
    public static void main(String[] args) {
        B b = new B();
    }
}
class A {

    public A() {
        System.out.println("a");
    }
    A(String name){
        System.out.println("a name");
    }
}class B {
    public B() {
        this("abc");//还能这样做
        System.out.println("b");
    }

    B(String name) {
        System.out.println(" b name");

    }
}//答案 a， b name， b

==================
继承实际应用
package com.hspedu.encapsulate.extend_.improve;

import com.xiao.C;

public class Computer {
    private String CPU;
    private int memory;
    private int Harddisk;


    public Computer(String CPU, int memory, int harddisk) {
        this.CPU = CPU;
        this.memory = memory;
        this.Harddisk = harddisk;
    }

    public String getCPU() {
        return CPU;
    }

    public void setCPU(String CPU) {
        this.CPU = CPU;
    }

    public int getMemory() {
        return memory;
    }

    public void setMemory(int memory) {
        this.memory = memory;
    }

    public int getHarddisk() {
        return Harddisk;
    }

    public void setHarddisk(int harddisk) {
        Harddisk = harddisk;
    }

    public void printInfo() {
        System.out.println("PC信息=");
        System.out.println(getDetail());
    }

    public String getDetail() {
      
        return "cpu=" + CPU + " " + "memory=" + memory + " " + "Harddis=" + Harddisk;
    }


}


class PC extends Computer {
    private String brand;

    //这里idea根据继承的规则，自动把构造器的调用写好
//这里也体现出：继承的基本思想，父类的构造器完成父类属性的初始化
    //子类的构造器完成子类属性初始化
    public PC(String CPU, int memory, int harddisk, String brand) {
        super(CPU, memory, harddisk);
        this.brand = brand;
    }

    public String getBrand() {
        return brand;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }public void printInfo(){
        System.out.println("PC信息");
        System.out.println(getDetail()+ "brand="+brand);
    }
}

class Test1 {
    public static void main(String[] args) {


        PC pc = new PC("intel", 16, 500, "IBM");
        pc.printInfo();

    }

}子类构造方法中可以同时出现super和this关键字吗？

可以同时出现

this是调用本类的属性和方法（构造方法），也可以调用父类的方法（构造方法除外）但是如果子类的方法和父类方法重名，那么this只能调用子类的哪个方法，如果想调用父类的方法，需要用super关键字

super是调用父类的方法（构造方法），

为什么可以同时出现？？？？？

在构造方法中只要this和super不是调用构造方法就可以同时并且多次使用，因此可以同时出现

不可以同时出现？？？？?

在同一个构造方法中只能调用一次其他构造方法，因此super和this不可同时使用（调用本类和父类的构造方法）
======================
再加一个notepad 继承 pc
package com.hspedu.encapsulate.extend_.improve;

public class Computer {
    private String CPU;
    private int memory;
    private int Harddisk;


    public Computer(String CPU, int memory, int harddisk) {
        this.CPU = CPU;
        this.memory = memory;
        this.Harddisk = harddisk;
    }

    public String getCPU() {
        return CPU;
    }

    public void setCPU(String CPU) {
        this.CPU = CPU;
    }

    public int getMemory() {
        return memory;
    }

    public void setMemory(int memory) {
        this.memory = memory;
    }

    public int getHarddisk() {
        return Harddisk;
    }

    public void setHarddisk(int harddisk) {
        Harddisk = harddisk;
    }

    

    public String getDetail() {

        return "cpu=" + CPU + " " + "memory=" + memory + " " + "Harddis=" + Harddisk;
    }


}


class PC extends Computer {
    private String brand;

    //这里idea根据继承的规则，自动把构造器的调用写好
//这里也体现出：继承的基本思想，父类的构造器完成父类属性的初始化
    //子类的构造器完成子类属性初始化
    public PC(String CPU, int memory, int harddisk, String brand) {
        super(CPU, memory, harddisk);
        this.brand = brand;
    }

    public String getBrand() {
        return brand;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }

    public String printInfo() {

        return "PC信息\n" + getDetail() + "brand=" + brand;
    }
}

class Notebook extends PC {
    String color;

    public Notebook(String CPU, int memory, int harddisk, String brand, String color) {
        super(CPU, memory, harddisk, brand);
        this.color = color;
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }

    public void printf() {
       
        System.out.println(printInfo() + "color=" + color);

    }
}

class Test1 {
    public static void main(String[] args) {


        Notebook notebook = new Notebook("intel", 16, 500, "IBM", "yello");

        notebook.printf();

    }

super代表父类的引用，用于访问父类的属性、方法、构造器
1.访问父类的属性、但不能访问父类的private属性
super.属性名
2.访问父类的方法，不能访问父类的private方法
super.方法名（参数列表）
3.访问父类的构造器（）：
super（参数列表）；只能放在构造器的第一句，只能出现一句


super给带来的好处：
调用父类的构造器的好处：（分工明确，
1.父类属性由父类初始化，子类的属性由子类初始化）
2.当子类中有和父类中的成员（属性和方法）重名时，为了访问父类的成员，必须通过super。如果没有重名，使用super、this、直接访问


package com.hspedu.encapsulate.super_;

public class A{
    //四种修饰符来修饰四个属性
    public int n1 = 100;
    protected int n2 = 200;
    int n3 = 300;
    private int n4 =400;
    public void m1(){//可以访问四个属性

        System.out.println("n1=" + n1 + "n2=" + n2 + "n3=" + n3 + "n4="+ n4);



    }//只有 默认和public可以修饰类

    public void cal(){
        System.out.println("cal");
    }
}



package com.hspedu.encapsulate.super_;

public class B extends A{
    public int n1 = 10;
    protected int n2 = 20;
    int n3 = 30;
    private int n4 =40;
    //1.访问父类的属性、但不能访问父类的private属性
    //super.属性名


    public void hi() {
        System.out.println(super.n1 +" "+super.n2+" "+super.n3);
    }


    public void cal() {
        System.out.println("b类的cal");
    }

    public void sum(){
        System.out.println("B类的sum()");
        //希望调用父类-A的cal方法
        //这时，因为子类B没有cal方法，因此我可以使用下面三种方式
        //找cal方法时，顺序是，先找本类，如果有，则调用，如果没有，则找父类（如果有并可以调用）
        //3.如果父类没有，则继续找父类的父类，整个规则，都是一样的，直到object
        //提示：如果查找方法的过程中，找到了，但是不能访问，则报错
        //     如国查找方法的过程中，没有找到，则提示方法不存在
//        cal();跟加this等价
//        this.cal();//找本类
        super.cal();//直接找父类
        System.out.println(super.n1);
        System.out.println(this.n1);//跟n1一样
        System.out.println(super.n2);
        System.out.println(this.n2);//跟n1一样
        System.out.println(super.n3);
        System.out.println(this.n3);//跟n1一样
//        System.out.println(super.n4);//n4显示错误
        System.out.println(this.n4);//跟n1一样
    }
}
package com.hspedu.encapsulate.super_;

public class super01 {
    public static void main(String[] args) {
        B b = new B();
        b.sum();
    }
}
结果：
B类的sum()
cal（是super）
100
10
200
20
300
30
40
b类的cal（this）


super关键字
super的访问不限于直接父类，如果爷爷类和本类中有同名的成员，也可以使用super去访问爷爷类的成员；如果多个基类中都有同名的成员，使用super访问遵循就近原则。A->B->C

super 和this比较

this：
访问属性：访问本类中的属性，如果本类没有此属性则从父类中继续查找
调用方法：访问本类中的方法，如果本类没有次方法则从父类继续查找
调用构造器：调用本类构造器，必须放在构造器的首行
特殊：表示当前对象
super：
访问属性：从父类开始查找的属性
调用方法：直接访问父类中的方法
调用构造器：调用父类构造器，必须放在构造器的首行
特殊：子类中范文父类对象











