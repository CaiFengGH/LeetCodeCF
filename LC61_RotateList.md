```
package Medium;

/**
 * @author Ethan
 * @desc rotate single list 
 */
public class LC61_RotateList {
	
	public ListNode rotateList(ListNode head,int k){
		//1-detect exception
		if(head == null || head.next == null) return head;
		
		//2-initate dummy: fast: slow:
		ListNode dummy = new ListNode(-1);
		dummy.next = head;
		ListNode fast = dummy, slow = dummy; 
		
		//3-initate len and move fast
		int len = 0;
		while(fast.next != null){ 
			fast = fast.next;
			len++;
		}
		
		//4-move slow
		for(int i = len - k % len; i > 0; i--){
			slow = slow.next;
		}
		
		//5-swap point
		fast.next = dummy.next;
		dummy.next = slow.next;
		slow.next = null;
		
		//6-return 
		return dummy.next;
	}
	
	/**
	 * @author Ethan
	 * @desc print single list 
	 */
	public void printList(ListNode head){
		ListNode cur = head;
		while(cur != null){
			System.out.print(cur.value + " ");
			cur = cur.next;
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC61_RotateList rl = new LC61_RotateList();
		ListNode a = new ListNode(0);
		ListNode b = new ListNode(1);
		ListNode c = new ListNode(2);
		ListNode d = new ListNode(3);
		ListNode e = new ListNode(4);
		a.next = b;
		b.next = c;
		c.next = d;
		d.next = e;
		
		System.out.println("before rotate:");
		rl.printList(a);
		
		ListNode newHead = rl.rotateList(a, 2);
		
		System.out.println("after rotate:");
		rl.printList(newHead);
	}
}

```
