```
package CaiFeng;

import java.util.Stack;

public class LC20_ValidParentheses {

	/**
	 * @author Ethan
	 * @desc 满足两点：一个'('，一个')'，且必须'('先出现
	 */
	public boolean validParentheses(String s){
		Stack<Character> stack = new Stack<Character>();
		//左符号，则压栈
		for(char c: s.toCharArray()){
			if(c == '('){
				stack.push(')');
			}else if( c == '{'){
				stack.push('}');
			}else if( c == '['){
				stack.push(']');
			}
			//此时三种对称的符号
			else if(stack.isEmpty() || stack.pop() != c){
				return false;
			}
		}
		//若此时stack中仍然存在元素，则不满足
		return stack.isEmpty();
	}
}

```
