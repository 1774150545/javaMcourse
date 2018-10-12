相同点：   
　　Comparable<T> 和 Comparator<T>都是接口   
不同点：   
　　两者声明的方法不同。前者是compareTo()方法，后者是compare()方法。   
 
　　　　Comparable<T>此接口是由具体某个有实际意义的类来实现，指示出此类的对象有什么样的排序方法。下面的苹果

```
public class Apple implements Comparable<Apple> {
    /**
     * 苹果的重量
     */
    private int  weight;

    /**
     * 自然排序即从小到大
     * 返回1的，代表此对象比参数对象大，排在后面，这样就可以控制降序或升序排列
     */
    @Override
    public int compareTo(Apple apple) {
        if (this.weight > apple.getWeight())
        {
            return -1;
        }
        else if (this.weight < apple.getWeight())
        {
            return 1;
        }
        else
        {
            return 0;
        }
    }
}
```
上面的例子中，苹果重量轻的将排在后面，所以是降序排列。  

 
　　　　Comparator<T>此接口一般用来的定义比较器，不会由包含实际意义的类来实现，而是由具体比较器来实现。下面定义一个比较器：
```
public class WeightComparator implements Comparator<Apple> {
    /**
     * 苹果的重量
     */
    private int  weight;

    /**
     * 自然排序即从小到大
     * 返回1的，代表此对象比参数对象大，排在前面，这样就可以控制降序或升序排列
     */
    @Override
    public int compare(Apple a, Apple b) {
        if (a.getWeight() > b.getWeight())
        {
            return 1;
        }
        else if (a.getWeight() < b.getWeight())
        {
            return -1;
        }
        else
        {
            return 0;
        }
    }
    
    public static void main(String[] args)
    {
        Apple a = new Apple();
        Apple b = new Apple();
        Apple c = new Apple();
        a.setWeight(50);
        b.setWeight(150);
        c.setWeight(100);
        
        Apple[] apples = {a,b, c};
        Arrays.sort(apples, new WeightComparator());
        //50 100 150
        System.out.println("" + apples[0] + apples[1] + apples[2]);  
    }
}
```
上面的例子定义了一个重量比较器，我把它用来比较苹果的重量，即使用泛型  
public class WeightComparator implements Comparator<Apple>  
