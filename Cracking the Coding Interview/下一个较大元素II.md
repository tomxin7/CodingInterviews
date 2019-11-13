<a name="OXQ12"></a>
### 下一个较大元素II
**题目描述：（面试金典）** <br />现在有一个数组，请找出数组中每个元素的后面比它大的最小的元素，若不存在则为-1。<br />给定一个int数组A及数组的大小n，请返回每个元素所求的值组成的数组。保证A中元素为正整数，且n小于等于1000。

**测试样例：**<br />[11,13,10,5,12,21,3],7<br />**返回：**<br />[12,21,12,12,21,-1,-1]<br />**代码：**
```
import java.util.*;

public class NextElement {
    public int[] findNext(int[] A, int n) {
        // write code here
        int[] arr=new int[n];
        for(int i=0;i<n;i++){
            int tem=Integer.MAX_VALUE;
            for(int j=i+1;j<n;j++){
                if(A[j]>A[i]){
                    if(tem>A[j])
                        tem=A[j];
                }
            }
            if(tem==Integer.MAX_VALUE)
                arr[i]=-1;
            else
                arr[i]=tem;
        }
        return arr;
    }
}
```
