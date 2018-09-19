package Easy;

/**
 * @author Ethan
 * @desc 验证单链表是否是回文单链表 
 */
public class LC234_PalindromeLinkedList {

	public boolean isPalindrome(ListNode head){
		//1-异常参数检测
		if(head == null){
			return false;
		}
		//2-基于快慢指针寻找中间节点
		ListNode slow = head; 
		ListNode fast = head; 
		while(fast != null && fast.next != null){
			slow = slow.next;
			fast = fast.next.next;
		}
		
		//3-奇数和偶数的区别
		if(fast != null){
			//奇数个fast不为null
			slow = slow.next;
		}
		
		//4-反转后一半
		slow = reverseLinkedList(slow);
		fast = head;
		//5-两个链表进行对比
		while(slow != null){
			if(slow.value != fast.value){
				return false;
			}
			slow = slow.next;
			fast = fast.next;
		}
		return true;
	}

	/**
	 * @author Ethan
	 * @desc 反转字符串 
	 */
	private ListNode reverseLinkedList(ListNode head) {
		ListNode pre = null; 
		ListNode next = null;
		while(head != null){
			next = head.next;
			head.next = pre;
			pre = head;
			head = next;
		}
		return pre;
	}
	
	/**
	 * @author Ethan
	 * @desc 打印单链表 
	 */
	public void printLinkesList(ListNode head){
		ListNode cur = head;
		while(cur != null){
			System.out.print(cur.value+"->");
			cur = cur.next;
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC234_PalindromeLinkedList pll = new LC234_PalindromeLinkedList();
		ListNode a = new ListNode(1);
		ListNode b = new ListNode(2);
		ListNode c = new ListNode(3);
		ListNode d = new ListNode(1);
		a.next = b;
		b.next = c;
		c.next = d;
		
		pll.printLinkesList(a);
		
		boolean isPalindrome = pll.isPalindrome(a);
		
		System.out.println(isPalindrome);
	}
}
