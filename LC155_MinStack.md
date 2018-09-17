```
package CaiFeng;

import java.util.Stack;

/**
 * @author Ethan
 */
public class LC155_MinStack {
	
	    private int min = Integer.MAX_VALUE;
	    private Stack<Integer> stack;
	
	    public LC155_MinStack() {
		stack = new Stack<Integer>();
	    }

	    public void push(int x) {
		if(x <= min){
			stack.push(min);
			min = x;
		}
		stack.push(x);
	    }

	    public void pop() {
		if(stack.pop() == min){
			min = stack.pop();
		}
	    }

	    public int top() {
		return stack.peek();
	    }

	    public int getMin() {
		return min;
	    }
}

```
