---
title: 001java网络编程
date: 2020-07-18 09:10:27
tags:
---
1. UML：统一建模语言

2. 面向对象的基本思想之一是封装实现细节并且公开接口。在java语言中采用了访问控制修饰符来  控制类，以及类的方法和变量的访问权限，从而达到隐藏实现细节值暴露接口的能力。

3. 访问控制修饰符：公开级别：用 public 修饰，对外公开   。受保护级别：用 protected 修饰，向子类及同一个包中的类公开。默认级别：没有访问修饰符，向同一个包中的类公开。私有级别：用 private 修饰，只有类本身可以访问，不对外公开

4. 封装：把对象的属性隐藏起来，只能通过公开的方法来得到或者设置属性值，默认getter，setter方法。

5. 方法内的变量不能使用修饰符，方法内不能新建方法。

6. 静态常量：特点：我们强调过常量的特点是不需要实例化，在 Java 当中实际上是创建了一个全局唯一的内存空间并且分配给了这个变量。所以常量的值只会随 Java 的销毁才会被销毁，这样也就方便我们存储一些数据到内存中，否则会随着对象的销毁被销毁掉的。使用场景：常用的字符串值，例如：public static final String USER_KEY = "123456" ，final：USER_KEY在后续操作不可更改。需要在内存做还缓存的值。例如：public static List<School> SCHOOLS = new ArrayList<>();

7. 继承extends：方法覆盖。调用父类的方法:super，构造函数里的super方法必写在第一行。子类运用 super 调用父类一般会发生在父类有一些通用的逻辑可以被执行。随着我们后面项目的深入会逐渐理解这句话的概念。当父类只有一个有参数的构造函数的时候，子类也必须要具备这个构造函数，或者调用super方法来实现新的构造函数。注：无参构造函数是默认的，所以子类没有要求，但其是也是有的,子类的无参构造函数和super()都是默认的，可省略。

8. 接口interface：我们定义接口的名称遵循 XxxService。问：例如我定义了一个接口，但是我在继承这个接口的类中还要写接口的实现方法，那我不如直接就在这个类中写实现方法岂不是更便捷，还省去了定义接口？答：1.接口是规范、标准，是大家都知道这个是做什么的，但是不用知道具体怎么做，就像你知道麦当劳买汉堡，你会吃就行啦，不需要知道汉堡怎么做出来。2.接口可以反复调用，拥有良好的扩展性。就像门口开了一家新的麦当劳，你就大致知道他卖啥，如果需要详细知道，才进去看一下就行。3.接口可以减少代码的耦合，降低沟通成本。

9. 接口实现类implements：实现类的命名规则是XxxServiceImpl。规则：接口定义的方法在实现类里必须要全部实现了，而且方法签名要一模一样（同样的方法名称、方法参数、方法返回值）<由于接口定义的方法都是 <code>public</code> 的，所以实现类的方法控制修饰符也必须是 <code>public</code>。
   import com.youkeda.service.RoleService;
   import com.youkeda.service.impl.RoleServiceImpl;
   RoleService roleService = new RoleServiceImpl();

10. java常用接口：Map存储这种键值对的数据，也是一种结合数据：
    import java.util.Map;
    import java.util.HashMap;// key value 得是 Java 类型
    Map<key,value> map = new HashMap<>();
    map.put(1,"Monday");
    String weekText = map.get(3);
    int size = map.size();
    Map的遍历：遍历字符串
    for (Map.Entry<Integer,String> entry : map.entrySet()){ 
       System.out.println("Key = " + entry.getKey() + 
                      ", Value = " + entry.getValue());
     }

    for(Integer key:  map.keySet()){

}
    

    List支持同一类型的集合存储：
    List<String> strings = new ArrayList<>();

11. 运行错误 的抛出，捕获，。例：Exception in thread "main" java.lang.NullPointerException
      at ExceptionTest2.getStrLength(ExceptionTest2.java:17)
      at ExceptionTest2.main(ExceptionTest2.java:8。这个错误就比较复杂啦，我经常遇到的错误一般是这样的。为什么复杂呢？因为代码必须运行后，才会出现。我们会把这种运行时出现的错误称为异常，因为是运行时出现的错误，所以异常也是可以被我们处理的，这个处理行为就叫捕获，这个词很形象：某个bug的出现抛出了异常，需要我们去捕获它，如果不捕获，程序就会坏了。抛出异常throws Exception。 throw new Exception("姓名不能为空");
      try {
          int len = getStrLength(null);
      } catch (NullPointerException e) {
          int len = 0;
      }finally{      关门    }
      自定义异常
      package com.youkeda.exception;

      public class ParamNullException extends Exception {

    ​       public ParamNullException() {
    ​        }

      }

12. 内部类：外部类调用实例内部类需要先实例化  。静态内部类可以直接被调用，需要实例化，不需要线实例化外部类。需要导内部包。局部内部类：方法内部的类。

13. 匿名类：使用比较频繁，本质上是一个局部内部类。不同的是匿名类只用于类的实例化，而不是声明。
    public class ATest {  
    public static void main(String[] args){    
      A a = new A(){      
        public void method(){        
          System.out.println("执行内部类");      
          }   
        };    
        a.method();  }}

14. 抽象类abstract：首先是一个父类

15. **实例化的前提是构造函数。**

16. List与数组的转换  Arrays：
    import java.util.Arrays;
    import java.util.List;
    数组转化为列表
    List<Integer> lists = Arrays.asList("小王","小明","小李");
    列表转化成字符串
    String string = String.join(",", list);
    列表长度，集e't合求长度.size(),添加add(),获取get()
    int size = list.size();String string = lists.get(1),lists.add();
    列表转化为数组
    List<Integer> al = new ArrayList<Integer>();
    Integer[] arr = al.toArray(new Integer[]{})
    字符串转化为数组
    String str = "Rahul,Utkarsh,Shubham,Neelam";
    String[] array = str.split(",");

17. 排序：数组Arrays.sort(intArr内部只有一种类型的数据，;集合Collections.sort()
    数组自定义排序
     Arrays.sort(intArr, new Comparator<Integer>(){           
      public int compare(Integer o1, Integer o2){        
      // 判断 o2>o1，执行降序排序               
     return o2-o1;            
     }        });
    集合的排序
     // 实现升序排序
    Collections.sort(ar, new Comparator<Student>(){
      public int compare(Student a, Student b) { 
        // 第一个参数的学号 > 第二个参数的学号
        return a.getRollNo() - b.getRollNo(); 
      } 
    }); 

18. 问：集合为什么不能直接用println直接输出？原因：集合里面含有不同的数据类型，解决方法：如果需要输出内部数据，需要修改toString()方法。因为println输出是默认调用toString()方法，只能输出同一类型的，所以toString()方法需要重写。

19. 集合的操作： // 删除第4条记录list.remove(3);// 合并 list2 到 list1 集合中 list1.addAll(list2);//截取 List<String> arrlist2 = list.subList(2, 4);

20. 静态方法调用非静态方法需要实例化

    



