```
package CaiFeng;

import java.util.Stack;

/**
 * @author Ethan
 */
public class LC232_MyQueue {
	
	private Stack<Integer> stackPush;
	private Stack<Integer> stackPop;
	
	public LC232_MyQueue(){
		stackPush = new Stack<Integer>();
		stackPop = new Stack<Integer>();
	}
	
	public void push(int x) {
		stackPush.push(x);
	}
	    
    public int pop() {
        peek();
    	return stackPop.pop();
    }
    
    public int peek() {
    	if(stackPop.empty()){
    		while(!stackPush.empty()){
    			stackPop.push(stackPush.pop());
    		}
    	}
        return stackPop.peek();
    }
    
    public boolean empty() {
        return stackPush.empty() && stackPop.empty();
    }
}

```
