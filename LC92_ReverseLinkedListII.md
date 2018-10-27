```
package Medium;

/**
 * @author Ethan
 * @desc 
 * reverse linked list from position-from to position-to
 * 1-2-3-4-5 2 4 -> 1-4-3-2-5
 * 1-2-3-4-5 1 4 -> 4-3-2-1-5
 */
public class LC92_ReverseLinkedListII {

	public ListNode reverseLinkedList(ListNode head,int from,int to){
		//1-initate fPre: tPos: len: node:
		ListNode fPre = null; 
		ListNode tPos = null;
		ListNode node = head;
		int len = 0;
		
		while(node != null){
			len++;
			if(len == from - 1){
				fPre = node;
			}
			if(len == to + 1){
				tPos = node;
			}
			node = node.next;
		}
		
		//2-detect exception
		if(from > to || from < 1 || to > len){
			return head;
		}
		
		//3-swap listNode.next
		node = fPre == null ? head : fPre.next;
		ListNode node1 = node.next;
		node.next = tPos;
		ListNode next = null;
		
		while(node1 != tPos){
			next = node1.next;
			node1.next = node;
			node = node1;
			node1 = next;
		}
		
		//4-special case
		if(fPre != null){
			fPre.next = node;
			return head;
		}
		
		//5-return
		return node;
	}
	
	public void printLinkedList(ListNode head){
		ListNode cur = head; 
		while(cur != null){
			System.out.print(cur.value+" ");
			cur = cur.next;
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC92_ReverseLinkedListII rl = new LC92_ReverseLinkedListII();
		ListNode a = new ListNode(1);
		ListNode b = new ListNode(2);
		ListNode c = new ListNode(3);
		ListNode d = new ListNode(4);
		ListNode e = new ListNode(5);
		a.next = b;
		b.next = c;
		c.next = d;
		d.next = e;
		
		System.out.println("before reverse:");
		rl.printLinkedList(a);
		
		System.out.println("after reverse:");
		ListNode newHead = rl.reverseLinkedList(a, 1, 4);
		rl.printLinkedList(newHead);
	}
}

```
