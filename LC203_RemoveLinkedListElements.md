```
package Easy;

public class LC203_RemoveLinkedListElements {

	/**
	 * @author Ethan
	 * @desc 移除单链表中重复的节点
	 */
	public ListNode removeElements(ListNode head,int value){
		//1-初始化
		ListNode dummy = new ListNode(-1);
		dummy.next = head;
		ListNode pre = dummy;
		ListNode cur = head;
		//2-遍历删除节点
		while(cur != null){
			if(cur.value == value){
				pre.next = cur.next;
			}else{
				pre = pre.next;
			}
			cur = cur.next;
		}
		return dummy.next;
	}
	
	/**
	 * @author Ethan
	 * @desc 打印单链表
	 */
	public void printList(ListNode head){
		ListNode cur = head;
		while(cur != null){
			System.out.print(cur.value+"->");
			cur = cur.next;
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC203_RemoveLinkedListElements remove = new 
				LC203_RemoveLinkedListElements(); 
		ListNode a = new ListNode(6);
		ListNode b = new ListNode(2);
		ListNode c = new ListNode(6);
		ListNode d = new ListNode(3);
		ListNode e = new ListNode(6);
		
		a.next = b;
		b.next = c;
		c.next = d;
		d.next = e;
		
		remove.printList(a);
		
		ListNode res = remove.removeElements(a, 6);
		
		remove.printList(res);
		
	}
}
```
