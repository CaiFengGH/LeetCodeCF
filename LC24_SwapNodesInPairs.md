```
package Medium;

/**
 * @author Ethan
 * @desc 在单链表中成对交换节点 
 */
public class LC24_SwapNodesInPairs {

	/**
	 * @author Ethan
	 * @desc 成对交换
	 */
	public ListNode swapPairs(ListNode head){
		//1-异常参数检测
		if(head == null || head.next == null){
			return head;
		}
		
		//2-初始化dumy: cur:
		ListNode dumy = new ListNode(0);
		dumy.next = head;
		ListNode cur = dumy;
		
		//3-遍历 
		while(cur.next != null && cur.next.next != null){
			//4-记录节点
			ListNode first = cur.next;
			ListNode second = cur.next.next;
			cur.next = second;
			first.next = second.next;
			cur.next.next = first;
			//5-更改节点指向
			cur = cur.next.next;
		}
		//5-返回新节点
		return dumy.next;
	}
	
	/**
	 * @author Ethan
	 * @desc 打印单链表
	 */
	public void printLinkedList(ListNode head){
		ListNode cur = head;
		while(cur != null){
			System.out.print(cur.value);
			cur = cur.next;
			if(cur != null){
				System.out.print("->");
			}
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC24_SwapNodesInPairs swap = new LC24_SwapNodesInPairs(); 
		ListNode a = new ListNode(1);
		ListNode b = new ListNode(2);
		ListNode c = new ListNode(3);
		ListNode d = new ListNode(4);
		a.next = b;
		b.next = c;
		c.next = d;
		swap.printLinkedList(a);
		ListNode res = swap.swapPairs(a);
		swap.printLinkedList(res);
	}
}

```
