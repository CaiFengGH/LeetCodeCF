```
package Medium;

/**
 * @author Ethan
 * @desc 
 * remove duplicate value, left distinct value
 */
public class LC82_RemoveDuplicateFromSortedList {

	/**
	 * @author Ethan
	 * @desc 
	 * based on two pointer
	 */
	public ListNode removeDuplicate(ListNode head){
		//1-detect exception
		if(head == null) return head;
		
		//2-initate dummy, slow and fast
		ListNode dummy = new ListNode(0);
		ListNode slow = dummy, fast = head; 
		slow.next = head;
		
		//3-fast and slow forward
		while(fast != null){
			while(fast.next != null && fast.value == fast.next.value){
				fast = fast.next;
			}
			
			if(slow.next != fast){
				slow.next = fast.next;
				fast = slow.next;
			}else{
				slow = slow.next;
				fast = fast.next;
			}
		}
		
		//4-return
		return dummy.next;
	}
	
	public void printList(ListNode head){
		ListNode cur = head;
		while(cur != null){
			System.out.print(cur.value + " ");
			cur = cur.next;
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC82_RemoveDuplicateFromSortedList remove = 
				new LC82_RemoveDuplicateFromSortedList(); 

		ListNode a = new ListNode(1);
		ListNode b = new ListNode(2);
		ListNode c = new ListNode(3);
		ListNode d = new ListNode(3);
		ListNode e = new ListNode(4);
		ListNode f = new ListNode(5);
		a.next = b;
		b.next = c;
		c.next = d;
		d.next = e;
		e.next = f;
		
		ListNode g = new ListNode(1);
		ListNode h = new ListNode(1);
		ListNode i = new ListNode(1);
		ListNode j = new ListNode(2);
		ListNode k = new ListNode(3);
		g.next = h;
		h.next = i;
		i.next = j;
		j.next = k;
		
		System.out.println("linked list 1:");
		remove.printList(a);
		
		System.out.println("after remove");
		ListNode newHead = remove.removeDuplicate(a);
		remove.printList(newHead);
		
		System.out.println("linked list 2:");
		remove.printList(g);
		
		System.out.println("after remove");
		newHead = remove.removeDuplicate(g);
		remove.printList(newHead);
	}
}

```
