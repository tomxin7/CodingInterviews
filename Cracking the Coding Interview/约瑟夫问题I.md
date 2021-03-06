### 约瑟夫问题I
**题目描述：（面试金典）**<br />约瑟夫问题是一个非常著名的趣题，即由n个人坐成一圈，按顺时针由1开始给他们编号。然后由第一个人开始报数，数到m的人出局。现在需要求的是最后一个出局的人的编号。<br />给定两个int n和m，代表游戏的人数。请返回最后一个出局的人的编号。保证n和m小于等于1000。<br />**测试样例：**<br />5 3<br />**返回：**<br />4 

**思路：**<br />把n个人的编号改为0~n-1，然后对删除的过程进行分析。<br />第一个删除的数字是(m-1)%n，记为k，则剩余的编号为(0,1,...,k-1,k+1,...,n-1)，下次开始删除时，顺序为(k+1,...,n-1,0,1,...k-1)。<br />用f(n,m)表示从(0~n-1)开始删除后的最终结果。<br />用q(n-1,m)表示从(k+1,...,n-1,0,1,...k-1)开始删除后的最终结果。<br />则f(n,m)=q(n-1,m)。<br />下面把(k+1,...,n-1,0,1,...k-1)转换为(0~n-2)的形式，即<br />k+1对应0<br />k+2对于1<br />...<br />k-1对应n-2<br />转化函数设为p(x)=(x-k-1)%n, p(x)的逆函数为p^(x)=(x+k+1)%n。<br />则f(n,m)=q(n-1,m)=p^(f(n-1,m))=(f(n-1,m)+k+1)%n，又因为k=(m-1)%n。<br />f(n,m)=(f(n-1,m)+m)%n;<br />最终的递推关系式为<br />f(1,m) = 0;                        (n=1)<br />f(n,m)=(f(n-1,m)+m)%n; （n>1）<br />代码
```
import java.util.*;

public class Joseph {
    /*
     * 编号为(0~n-1)
     */
    public int getResult(int n, int m) {
        if (n < 0 || m < 0) {
            return -1;
        }
        int last = 0;
        for(int i=2;i<=n;++i){
            last = (last+m)%i;
        }
        // 因为实际编号为(1~n)
        return (last+1);
    }
}
```