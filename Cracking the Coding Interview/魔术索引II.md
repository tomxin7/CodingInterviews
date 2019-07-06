<a name="aO8tC"></a>
### 魔术索引II
**题目描述：（面试金典）**<br />在数组A[0..n-1]中，有所谓的魔术索引，满足条件A[i]=i。给定一个不下降序列，元素值可能相同，编写一个方法，判断在数组A中是否存在魔术索引。请思考一种复杂度优于o(n)的方法。<br />给定一个int数组A和int n代表数组大小，请返回一个bool，代表是否存在魔术索引。<br />**测试样例：**<br />[1,1,3,4,5]<br />**返回：**<br />true<br />**代码**
```
import java.util.*;

public class MagicIndex {

public boolean findMagicIndex(int[] A, int n) {
    for (int i = 0; i < n; ) {
        if (A[i] == i) {
            return true;
        } else {
            i = Math.max(A[i], i + 1);
        }
    }
 
    return false;
}
}
```