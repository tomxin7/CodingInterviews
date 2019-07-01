<a name="0MfGb"></a>
### 机器人走方格I
**题目描述：（面试金典）**<br />有一个XxY的网格，一个机器人只能走格点且只能向右或向下走，要从左上角走到右下角。请设计一个算法，计算机器人有多少种走法。给定两个正整数int x,int y，请返回机器人的走法数目。保证x＋y小于等于12。

**测试样例：**<br />2,2<br />**返回：**<br />2<br />**思路：**<br />题目要求走的是大格子而不是网格线的交点，所以有两种走法。<br />二维数组用于计算走到当前格子的走法总数，为其上方格子走法总数与其左侧格子走法总数之和

```java
import java.util.*;

public class Robot {

public int countWays(int x, int y) {
        // write code here
        int[][] dp = new int[13][13];
        for (int i = 1; i < y; i++)
            dp[0][i] = 1;
         
        for (int i = 1; i < x; i++)
            dp[i][0] = 1;
         
        for (int i = 1; i < x; i++)
            for (int j = 1; j < y; j++)
                dp[i][j] = dp[i-1][j] + dp[i][j-1];
         
        return dp[x-1][y-1];
    }
}
```