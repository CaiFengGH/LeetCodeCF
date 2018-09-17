```
package CaiFeng;

import java.util.HashMap;

/**
 * @author Ethan
 */
public class LC141_ListHoop {

	/**
	 * @author Ethan
	 */
	public boolean hasLoop(ListNode head){
		if(head == null){
			return false;
		}
		
		ListNode slow = head;
		ListNode fast = head;
		
		while(fast != null){
			slow = slow.next;
			fast = fast.next;
			if(fast == null){
				return false;
			}
			fast = fast.next;
			if(fast == null){
				return false;
			}
			if(fast.val == slow.val){
				return true;
			}
		}
		return false;
	}
	
	/**
	 * @author Ethan
	 */
	public boolean hasLoop2(ListNode head){
		ListNode curr = head;
		HashMap<ListNode,ListNode> hash = new HashMap<ListNode,ListNode>();
		while(curr != null){
			if(hash.get(curr) != null){
				return true;
			}else{
				hash.put(curr, curr);
			}
			curr = curr.next;
		}
		return false;
	}
}

```
