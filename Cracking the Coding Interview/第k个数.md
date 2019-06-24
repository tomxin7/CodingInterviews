<a name="PZqpU"></a>
### 第k个数
**题目描述：（面试金典）**<br />有一些数的素因子只有3、5、7，请设计一个算法，找出其中的第k个数。给定一个数int k，请返回第k个数。保证k小于等于100。

**测试样例：**<br />3<br />**返回：**<br />7<br />**思路：**<br />每个数都是找三个数中最小的数*3或5或7得出来的
```java
import java.util.*;

public class KthNumber {

    public int findKth(int k) {
        int [] array =new int[k];
        int num3=0;
        int num5=0;
        int num7=0;
        array[0]=3;
        array[1]=5;
        array[2]=7;
        for(int i=3;i<k;i++){
            array[i]=Math.min(Math.min(array[num3]*3,array[num5]*5),array[num7]*7);
            if(array[i]==array[num3]*3) num3++;
            if(array[i]==array[num5]*5) num5++;
            if(array[i]==array[num7]*7) num7++;
        }
        return array[k-1];
    }
}
```