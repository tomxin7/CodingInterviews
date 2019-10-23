<a name="7Z8dF"></a>
### 无判断max
**题目描述：（面试金典）** <br />请编写一个方法，找出两个数字中最大的那个。条件是不得使用if-else等比较和判断运算符。给定两个int a和b，请返回较大的一个数。若两数相同则返回任意一个。<br />**测试样例：**<br />1，2<br />**返回：**<br />2<br />**代码：**
```java
import java.util.*;

public class Max {
    public int getMax(int a, int b) {
        return a - b > 0 ? a : b;
    }
}
```