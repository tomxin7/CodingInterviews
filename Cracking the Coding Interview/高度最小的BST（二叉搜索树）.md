

题目描述：（面试金典）<br />对于一个元素各不相同且按升序排列的有序序列，请编写一个算法，创建一棵高度最小的二叉查找树。给定一个有序序列int[] vals,请返回创建的二叉查找树的高度。<br />思路：<br />取巧的算法，因为序列是有序的，所以最小的二叉树是不断除以二。
```java
import java.util.*;

public class MinimalBST {
    public int buildMinimalBST(int[] vals) {
        int len = vals.length;
        int t = 0;
        while (len > 0){
            t++;
            len /= 2;
        }
        return t;
    }
}
```

<a name="63db5605"></a>


