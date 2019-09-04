**题目描述：（面试金典）**<br />请设计一种算法，解决著名的n皇后问题。这里的n皇后问题指在一个nxn的棋盘上放置n个棋子，使得每行每列和每条对角线上都只有一个棋子，求其摆放的方法数。<br />给定一个int n，请返回方法数，保证n小于等于15<br />**测试样例：**<br />1<br />**返回：**<br />1

```
import java.util.*;
 
public class Queens {
    public int nQueens(int n) {
        if (n<0) return 0;
        // write code here
        int[] record = new int[n];
        return process(0, record, n);
         
    }
     
    private int process(int i, int[] record, int n){
        if (i == n)
            return 1;
         
        int res = 0;
         
        for (int j=0; j<n; j++){
            if (isValid(record, i, j)){
                record[i] = j;
                res += process(i+1, record, n);
            }
        }
        return res;
    }
     
    private boolean isValid(int[] record, int i, int j){
        for (int k=0; k<i; k++){
            // 若在同一列或者对角线则返回false
            if (j == record[k] || Math.abs(record[k] - j) == Math.abs(k - i)) return false;
        }
        return true;
    }
}
```
