1、深拷贝与浅拷贝的区别
使用浅拷贝在拷贝对象的时候会复制对象本身以及基本类型成员变量，如果包含引用类型的成员变量则智慧复制其地址值
```java
  public  class  Person implement Cloneable{
  int age ;
  String name;
  Street street;
  @override 
    public Obeject  clone throws CloneNotSupportedException {
    //浅拷贝
      return  super.clone();
    }
  public class Address{
    private address
  }
  }
  public  class  Person implement Cloneable{
  int age ;
  String name;
  Street street;
  @override 
    public Obeject  clone throws CloneNotSupportedException {
    //深拷贝
      Person cloned = (Person) super.clone();
     cloned.adress = new Adress(this.address.getAdress());
     return  cloned;
    }
  public class Address implement{
    private String  address
    Adress(adress){
      this.adress = adress;
    }
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    
  }
  }
```
2、集合 map set list那些
3、循环依赖怎么解决
4、arrylist linklist（双向链表） 的数据数据结构 都实现了LIST接口通过add remove 增加和删除数据
首先 linklist基于链表由Node组成每一个node包括一数据域和指向下一个节点的指针，他的特点对内存的要求比较灵活不像数组那样需要在内存中连续存储 ，便于插入，删除，时间复杂度为O(1)
而arraylist是基于数组实现的在数组的末尾插入和删除时空复杂度为O(1),其他未O（N）

#### 5、表的设计范式
##### 第一范式
要求表中的所有字段都是原子性的
每一列都是不可再分数据项
每一行都要有唯一性通过主键
表中的字段类型要相同
##### 第二范式
要满足第一范式
所有的非主键属性要完全依赖主键 
##### 第三范式
满足第二范式
并且不存在传递依赖即其他非主属性不依赖且他非主属性
##### 第四范式
满足第三范式
不存在多值依赖X->->Y其中X是R中的一个候选建
[](url)
StudentID | ClubName | ActivityDate
-----------------------------------
1         | Chess    | 2023-04-01
1         | Chess    | 2023-04-08
1         | Soccer   | 2023-04-02
2         | Chess    | 2023-04-01
2         | Soccer   | 2023-04-03
在这个表中，存在多值依赖，因为对于同一个学生ID（StudentID），可以有多个俱乐部名称（ClubName）和活动日期（ActivityDate）的组合。为了满足第四范式，我们需要将这个表拆分成至少两个表：

学生俱乐部表（StudentClub）:
  学生ID（StudentID）
  俱乐部名称（ClubName）
俱乐部活动表（ClubActivity）:
  俱乐部名称（ClubName）
  活动日期（ActivityDate）
