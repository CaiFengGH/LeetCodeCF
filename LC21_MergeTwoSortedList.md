```
package CaiFeng;

/**
 * @author Ethan
 * @desc 
 */
public class LC21_MergeTwoSortedList {

	/**
	 * @author Ethan
	 */
	public ListNode mergeSortedList(ListNode head1,ListNode head2){
		if(head1 == null || head2 == null){
			return head1 == null ? head2 : head1; 
		}
		ListNode newHead = head1.value < head2.value ? head1 : head2;
		ListNode cur1 = newHead == head1 ? head1 : head2;
		ListNode cur2 = newHead == head1 ? head2 : head1;
		
		ListNode pre = null; 
		ListNode next = null; 
		
		while(cur1 != null && cur2 != null){
			if(cur1.value < cur2.value){
				pre = cur1;
				cur1 = cur1.next;
			}else{
				next = cur2.next;
				
				pre.next = cur2;
				cur2.next = cur1;
				
				pre = cur2;
				cur2 = next;
			}
		}
		pre.next = cur1 == null ? cur2 : cur1;
		return newHead;
	}
}

```
