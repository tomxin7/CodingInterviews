<a name="goXrI"></a>
### 机器人走方格II
**题目描述：（面试金典）**<br />有一个XxY的网格，一个机器人只能走格点且只能向右或向下走，要从左上角走到右下角。请设计一个算法，计算机器人有多少种走法。注意这次的网格中有些障碍点是不能走的。<br />给定一个int[][] map(C++ 中为vector >),表示网格图，若map[i][j]为1则说明该点不是障碍点，否则则为障碍。另外给定int x,int y，表示网格的大小。请返回机器人从(0,0)走到(x - 1,y - 1)的走法数，为了防止溢出，请将结果Mod 1000000007。保证x和y均小于等于50

```
import java.util.*;
/*
看到题目说防止溢出，然后我就不敢用递归了，那就迭代？一步步做，试试看吧
*/
public class Robot {
    public int countWays(int[][] map, int x, int y) {
        if(x==0||y==0) return 1;
        int array[][] =new int[x][y];
        if(map[0][0]==0||map[x-1][y-1]==0) return 0;//题目真的无聊，还把0.0点设成障碍物了。。
        array[0][0]=1;//开始在这里没有考虑清楚，一旦array[i][0]中有某个障碍物，那其后面均应该是0，而不是1
        for(int i=1;i<x;i++){//这里第一行和第一列的值要和后面的二维遍历分开设定，不然在二维数组的遍历中会存在数组越界
            if(map[i][0]==1) array[i][0]=array[i-1][0];//也可以用break的方式
            else  array[i][0]=0;
        }
        for(int j=1;j<y;j++){
            if(map[0][j]==1) array[0][j]=array[0][j-1];
            else  array[0][j]=0;
        }
         
        for(int i=1;i<x;i++){
            for(int j=1;j<y;j++){
                 array[i][j] =((map[i-1][j]==0?0:array[i-1][j])+(map[i][j-1]==0?0:array[i][j-1]))%1000000007;
            }
        }
        return array[x-1][y-1];
    }
}
```