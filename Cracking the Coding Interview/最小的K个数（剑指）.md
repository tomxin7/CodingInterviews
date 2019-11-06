<a name="opJYg"></a>
### 最小的K个数（剑指）
**题目描述**<br />输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。<br />**代码**<br />冒泡排序的思想，只不过最外层循环K次就可以了，也就是说不用全部排序，只挑出符合提议的K个就可以。冒泡排序的思想，只不过最外层循环K次就可以了，也就是说不用全部排序，只挑出符合提议的K个就可以。
```
public class Solution {
    public ArrayList<Integer> GetLeastNumbers_Solution(int [] input, int k) {
        ArrayList<Integer> list=new ArrayList<Integer>();
        ArrayList<Integer> list2=new ArrayList<Integer>();
        if(input==null||input.length==0||k==0||k>input.length)
            return list;
        TreeSet<Integer> set=new TreeSet<Integer>();
        for(int i=0;i<input.length;i++){
            set.add(input[i]);
        }
        Iterator<Integer> it = set.iterator(); 
        while (it.hasNext()) { 
          int x=it.next();
          list.add(x);
        } 
        for(int i=0;i<k;i++){
            list2.add(list.get(i));
        }
        return list2;
    }
}
```