---
date created: 2023-10-08 18:13
tags:
  - "#ArraryList添加、删除、查找元素"
  - "#ArraryList遍历"
  - "#ArrayList存储对象并遍历"
  - "#查找索引"
---

### 集合和数组的优势对比：

1. <mark style="background: #BBFABBA6;">长度可变</mark>
2. 添加数据的时候<mark style="background: #ABF7F7A6;">不需要考虑索引，默认将数据添加到末尾</mark>

### 1.1 ArrayList类概述

- 什么是集合

  ​ 提供一种存储空间<font color="#d99694">可变</font>的存储模型，存储的数据容量可以发生改变

- ArrayList集合的特点

  ​ 长度可以变化，<font color="#d99694">只能存储引用数据类型</font>。（如：String），_int等基本数据类型不行_

- 泛型的使用

  ​ 用于约束集合中存储元素的数据类型

### 1.2 ArrayList类常用方法
#### 1.2.1 构造方法
| 方法名                | 说明         |
| ------------------ | ---------- |
| public ArrayList() | 创建一个空的集合对象 |
#### 1.2.2 成员方法
| 方法名                               | 说明                  |   |
| --------------------------------- | ------------------- | - |
| public boolean add(要添加的元素)        | 将指定的元素追加到此集合的末尾     |   |
| public boolean remove(要删除的元素)     | 删除指定元素,返回值表示是否删除成功  |   |
| public E remove(int index)        | 删除指定索引处的元素，返回被删除的元素 |   |
| public E set(int index,E element) | 修改指定索引处的元素，返回被修改的元素 |   |
| public E get(int index)           | 返回指定索引处的元素          |   |
| public int size()                 | 返回集合中的元素的个数         |   |

#### 1.2.3 示例代码
#ArraryList添加、删除、查找元素
```java
public class ArrayListDemo02 {
    public static void main(String[] args) {
        //创建集合
        ArrayList<String> array = new ArrayList<String>();

        //添加元素
        array.add("hello");
        array.add("world");
        array.add("java");
        
		//删除元素（法1：删除指定的元素，返回删除是否成功）
        public boolean remove(Object o)：
            boolean result = array.remove("hello");
		//删除元素（法1：删除指定索引处的元素，返回被删除的元素）
        public E remove(int index)：删除指定索引处的元素，返回被删除的元素
            String result = array.remove(1);

		//修改元素
        public E set(int index,E element)：修改指定索引处的元素，返回被修改的元素
	        String result = array.set(2, "javaee");

		//查询元素
        public E get(int index)：返回指定索引处的元素
		    String s = array.get(0);  
			System.out.println("s:" + s);

        //public int size()：返回集合中的元素的个数
        System.out.println(array.size());

        //输出集合
        System.out.println("array:" + array);
    }
}
```

_输出结果
3
array:[hello, world, java]_

---
### 1.3 ArrayList存储字符串并遍历
#ArraryList遍历
#### 1.3.1 案例需求
​ 创建一个存储字符串的集合，存储3个字符串元素，使用程序实现在控制台遍历该集合
#### 1.3.2 代码实现

```java
public class ArrayListDemo3 {
    public static void main(String[] args) {
        //1.创建集合对象
        ArrayList<String> list = new ArrayList<>();

        //2.添加元素
        list.add("aaa");
        list.add("bbb");
        list.add("ccc");
        list.add("ddd");

        //3.遍历
        //快捷键: list.fori 正向遍历
        //list.forr 倒着遍历
        System.out.print("[");
        for (int i = 0; i < list.size(); i++) {
            //i 依次表示集合里面的每一个索引

            if(i == list.size() - 1){
                //最大索引
                System.out.print(list.get(i));
            }else{
                //非最大索引
                System.out.print(list.get(i) + ", ");
            }
        }
        System.out.print("]");
    }
}
```

_输出结果_\
_[aaa, bbb, ccc, ddd]_

---
### 1.4 ArrayList存储学生对象并遍历
#ArrayList存储对象并遍历
#### 1.4.1 案例需求
​ 创建一个存储学生对象的集合，存储3个学生对象，使用程序实现在控制台遍历该集合
#### 1.4.2 代码实现

```java
public class ArrayListDemo4 {
    public static void main(String[] args) {
        //1.创建集合对象，用来存储数据
        ArrayList<Student> list = new ArrayList<>();

        //2.创建学生对象
        Student s1 = new Student("zhangsan",16);
        Student s2 = new Student("lisi",15);
        Student s3 = new Student("wangwu",18);

        //3.把学生对象添加到集合中
        list.add(s1);
        list.add(s2);
        list.add(s3);

        //4.遍历
        for (int i = 0; i < list.size(); i++) {
            //i 依次表示集合中的每一个索引
            Student stu = list.get(i);
            System.out.println(stu.getName() + ", " + stu.getAge());
        }
    }
}
```
### 1.5 查找用户的索引
#查找索引
需求：
1. main方法中定义一个集合，存入三个用户对象。用户属性为：id，username，password
2. 要求：定义一个方法，根据id查找对应的学生信息。
   如果存在，返回索引
   如果不存在，返回-1

代码示例：
```java
public class ArrayListDemo6 {
    public static void main(String[] args) {
        /*需求：
        1，main方法中定义一个集合，存入三个用户对象。
        用户属性为：id，username，password
        2，要求：定义一个方法，根据id查找对应的学生信息。
        如果存在，返回索引
        如果不存在，返回-1*/


        //1.创建集合对象
        ArrayList<User> list = new ArrayList<>();

        //2.创建用户对象
        User u1 = new User("heima001", "zhangsan", "123456");
        User u2 = new User("heima002", "lisi", "1234");
        User u3 = new User("heima003", "wangwu", "1234qwer");

        //3.把用户对象添加到集合当中
        list.add(u1);
        list.add(u2);
        list.add(u3);

        //4.调用方法，通过id获取对应的索引
        int index = getIndex(list, "heima001");

        System.out.println(index);

    }


    //1.我要干嘛？  根据id查找对应的学生信息
    //2.我干这件事情需要什么才能完成？   集合 id
    //3.方法的调用处是否需要继续使用方法的结果？
    //要用必须返回，不要用可以返回也可以不返回
    //明确说明需要有返回值 int
    public static int getIndex(ArrayList<User> list, String id) {
        //遍历集合得到每一个元素
        for (int i = 0; i < list.size(); i++) {
            User u = list.get(i);
            String uid = u.getId();
            if(uid.equals(id)){
                return i;
            }
        }
        //因为只有当集合里面所有的元素都比较完了，才能断定id是不存在的。
        return -1;
    }
}
```
