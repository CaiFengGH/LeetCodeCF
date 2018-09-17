```
package CaiFeng;

/**
 * @author Ethan
 * @desc 反转单链表 
 */
public class LC206_ReverseLinkList {

	/**
	 * @author Ethan
	 * @desc 基于迭代方式：移动pre和curr
	 */
	public ListNode reverseLinkList(ListNode head){
		//1-初始化 pre和curr
		ListNode pre = null;
		ListNode curr = head;
		
		//2-遍历移动
		while(curr != null){
			ListNode next = curr.next;
			curr.next = pre;
			//3-实现水平移动
			pre = curr;
			curr = next;
		}
		return pre;
	}
	
	/**
	 * @author Ethan
	 * @desc 基于递归的方式
	 */
	public ListNode reverseLinkList1(ListNode head){
		//1-递归结束条件
		if(head == null || head.next == null){
			return head;
		}
		//返回的p一直被返回到最初
		ListNode p = reverseLinkList1(head.next);
		head.next.next = head;
		head.next = null;
		return p;
	}
}

```
