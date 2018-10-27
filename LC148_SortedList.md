```
package Medium;

/**
 * @author Ethan
 * @desc 
 * linked list merge sort
 */
public class LC148_SortedList {
	
	public ListNode listMergeSort(ListNode head){
		//1-detect exception
		if(head == null || head.next == null) return head;  
		//2-get middle
		ListNode mid = getMid(head);
		ListNode halfNext = mid.next;
		mid.next = null;
		return listMerge(listMergeSort(head),listMergeSort(halfNext));
		
	}

	/**
	 * @author Ethan
	 * @desc 
	 * 1-4
	 * 2-3-5
	 */
	public ListNode listMerge(ListNode a,ListNode b){
		//1-initate cur: dummy:
		ListNode dummy = new ListNode(-1);
		ListNode cur = dummy;
		
		//2-compare and swap
		while(a != null && b != null){
			if(a.value <= b.value){
				cur.next = a;
				a = a.next;
			}else{
				cur.next = b;
				b = b.next;
			}
			cur = cur.next;
		}
		//3-exception
		cur.next = a == null ? b : a;
		//4-return
		return dummy.next;
	}
	
	/**
	 * @author Ethan
	 * @desc 
	 * based on two pointer
	 */
	private ListNode getMid(ListNode head) {
		ListNode fast = head;
		ListNode slow = head;
		
		while(fast.next != null && fast.next.next != null){
			fast = fast.next.next;
			slow = slow.next;
		}
		return slow;
	}

	public void printLinkedList(ListNode head){
		ListNode cur = head;
		while(cur != null){
			System.out.print(cur.value);
			cur = cur.next;
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC148_SortedList sl = new LC148_SortedList();
		ListNode a = new ListNode(1);
		ListNode b = new ListNode(3);
		ListNode c = new ListNode(4);
		ListNode d = new ListNode(2);
		ListNode e = new ListNode(5);
		
		a.next = b;
		b.next = c;
		c.next = d;
		d.next = e;
		
		System.out.println("before sort:");
		sl.printLinkedList(a);
		
		System.out.println("after sort:");
		ListNode newHead = sl.listMergeSort(a);
		sl.printLinkedList(newHead);
	}
}

```
