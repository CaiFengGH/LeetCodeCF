```
package CaiFeng;

import java.util.LinkedList;
import java.util.Queue;

/**
 * @author Ethan
 * @desc 使用两个队列实现栈 
 */
public class LC225_MyStackByQueue {

	//q1作为元素存储，q2作为中介
	private Queue<Integer> q1 = null;
	private Queue<Integer> q2 = null;
	
	public LC225_MyStackByQueue(){
		q1 = new LinkedList<Integer>();
		q2 = new LinkedList<Integer>();
	}
	
	public void push(int x){
		q1.offer(x);
	}
	
	public int pop(){
		while(q1.size() > 1){
			q2.offer(q1.poll());
		}
		int x = q1.poll();
		Queue<Integer> q = q1;
		q1 = q2;
		q2 = q;
		return x;
	}
	
	public int top(){
		while(q1.size() > 1){
			q2.offer(q1.poll());
		}
		int x = q1.poll();
		q2.offer(x);
		Queue<Integer> q = q1;
		q1 = q2;
		q2 = q;
		return x;
	}
	
	public boolean isEmpty(){
		return q1.size() == 0;
	}
}

```
