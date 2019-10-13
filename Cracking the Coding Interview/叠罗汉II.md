<a name="oNOqM"></a>
### 叠罗汉II
**题目描述：（面试金典）**<br />叠罗汉是一个著名的游戏，游戏中一个人要站在另一个人的肩膀上。为了使叠成的罗汉更稳固，我们应该让上面的人比下面的人更轻一点。现在一个马戏团要表演这个节目，为了视觉效果，我们还要求下面的人的身高比上面的人高。请编写一个算法，计算最多能叠多少人，注意这里所有演员都同时出现。<br />给定一个二维int的数组actors，每个元素有两个值，分别代表一个演员的身高和体重。同时给定演员总数n，请返回最多能叠的人数。保证总人数小于等于500。<br />**测试样例：**<br />[[1,2],[3,4],[5,6],[7,8]],4<br />**返回：**<br />4<br />**代码：**
```java
import java.util.*;

public class Stack {
    public int getHeight(int[][] actors, int n) {
        // write code here
        for(int i=1; i<n; i++){
            for(int j=0; j<n-i; j++){
                if(actors[j][0]>actors[j+1][0]){
                    int temp=temp=actors[j][0];
                    actors[j][0]=actors[j+1][0];
                    actors[j+1][0]=temp;
                     
                    temp=temp=actors[j][1];
                    actors[j][1]=actors[j+1][1];
                    actors[j+1][1]=temp;
                }
            }
        }
        int[] dp=new int[n];
        dp[0]=1;
        for(int i=1; i<n; i++){
            dp[i]=1;
            for(int j=i-1; j>=0; j--){
                if(actors[j][1]<=actors[i][1] && dp[j]+1>dp[i])
                    dp[i]=dp[j]+1;
            }
        }
        int max=0;
        for(int elem: dp){
            if(max<elem)
                max=elem;
        }
        return max;
    }
}
```