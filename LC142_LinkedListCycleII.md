```
package Medium;

/**
 * @author Ethan
 * @desc 
 * return cycle entrynode
 * input:1-2-3-4-5-3
 * output:3
 */
public class LC142_LinkedListCycleII {

	/**
	 * @author Ethan
	 * @desc 
	 * based on two pointer
	 */
	public ListNode entryListNode(ListNode head){
		//1-detect exception
		if(head == null || head.next == null) return null;
		
		//2-initate
		ListNode fast = head;
		ListNode slow = head; 
		
		//3-iterate
		while(fast.next != null && fast.next.next != null){
			fast = fast.next.next;
			slow = slow.next;
			
			//4-if entryListNode exist
			if(fast == slow){
				fast = head;
				while(fast != slow){
					fast = fast.next;
					slow = slow.next;
				}
				return fast;
			}
		}
		
		return slow;
	}
	
	public static void main(String[] args) {
		LC142_LinkedListCycleII entry = new LC142_LinkedListCycleII();
		ListNode a = new ListNode(1);
		ListNode b = new ListNode(2);
		ListNode c = new ListNode(3);
		ListNode d = new ListNode(4);
		ListNode e = new ListNode(5);
		
		a.next = b;
		b.next = c;
		c.next = d;
		d.next = e;
		e.next = c;
		
		ListNode entryListNode = entry.entryListNode(a);
		System.out.println(entryListNode.value);
	}
}

```
