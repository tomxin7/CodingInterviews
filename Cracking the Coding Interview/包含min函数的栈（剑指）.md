<a name="rWa70"></a>
### 包含min函数的栈（剑指）
**题目描述：**<br />定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。<br />**思路：**<br />用一个栈data保存数据，用另外一个栈min保存依次入栈最小的数

比如，data中依次入栈，5,  4,  3, 8, 10, 11, 12, 1<br />      则min依次入栈，5,  4,  3，no,no, no, no, 1<br />no代表此次不如栈<br />每次入栈的时候，如果入栈的元素比min中的栈顶元素小或等于则入栈，否则不如栈。<br />**代码：**
```
import java.util.Stack;

public class Solution {
    Stack<Integer> data = new Stack<Integer>();
    Stack<Integer> min = new Stack<Integer>();
    Integer temp = null;
    public void push(int node) {
        if(temp != null){
            if(node <= temp ){
                temp = node;
                min.push(node);
            }
            data.push(node);
        }else{
            temp = node;
            data.push(node);
            min.push(node);
        }
    }
     
    public void pop() {
        int num = data.pop();
        int num2 = min.pop();
        if(num != num2){
           min.push(num2);
        }
    }
     
    public int top() {
        int num = data.pop();
        data.push(num);
        return num;
    }
     
    public int min() {
        int num = min.pop();
        min.push(num);
        return num;
    }
}
```