```
package Medium;

/**
 * @author Ethan
 * @desc 两个整数相加，整数以链表形式存在 
 */
public class LC2_AddTwoNum {
	
	/**
	 * @author Ethan
	 * @desc 基于链表遍历
	 */
	public ListNode addTwoNumByPoint(ListNode l1,ListNode l2){
		//1-异常参数检测
		if(l1 == null || l2 == null){
			return l1 == null ? l2 : l1;
		}
		//2-初始化 pre: newHead: carry: cur:
		ListNode pre = new ListNode(0);
		ListNode newHead = pre;
		ListNode cur = null; 
		int sum = 0;
		int carry = 0;
		
		//3-遍历相加
		while(l1 != null || l2 != null || carry != 0){
			sum = (l1 == null ? 0 : l1.value) + (l2 == null ? 0 : l2.value) + carry;
			
			cur = new ListNode(sum % 10);
			carry = sum / 10;
			
			pre.next = cur;
			pre = cur;
			
			l1 = (l1 == null) ? l1 : l1.next;
			l2 = (l2 == null) ? l2 : l2.next;
		}
		
		return newHead.next;
	}
	
	//--------以下是基于自己思路
	public ListNode addTwoNum(ListNode head1,ListNode head2){
		if(head1 == null || head2 == null){
			return head1 == null ? head2 : head1;
		}
		int num1 = listToInt(head1);
		int num2 = listToInt(head2);
		int res = num1 + num2;
		
		int remain = res % 10;
		res = res / 10;
		ListNode pre = new ListNode(remain); 
		ListNode newHead = pre;
		ListNode cur = null;
		
		while(res != 0){
			remain = res % 10;
			res = res / 10;
			cur = new ListNode(remain);
			pre.next = cur;
			pre = cur;
		}
		return newHead;
	}

	/**
	 * @author Ethan
	 * @desc 将以list格式的整数转换为整数 
	 */
	private int listToInt(ListNode head) {
		ListNode cur = head;
		int num = 0;
		int power = 0;
		
		while(cur != null){
			num += cur.value * Math.pow(10, power++);
			cur = cur.next;
		}
		return num;
	}

	private void printList(ListNode head) {
		ListNode cur = head;
		while(cur != null){
			System.out.print(cur.value+"->");
			cur = cur.next;
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC2_AddTwoNum add = new LC2_AddTwoNum();
		
		ListNode a = new ListNode(9);
		ListNode b = new ListNode(1);
		ListNode c = new ListNode(9);
		ListNode d = new ListNode(9);
		ListNode e = new ListNode(9);
		ListNode f = new ListNode(9);
		
		System.out.println("add num1");
		add.printList(a);
		
		b.next = c;
		c.next = d;
		d.next = e;
		e.next = f;

		System.out.println("add num2");
		add.printList(b);
		
		ListNode newHead = add.addTwoNumByPoint(a, b);
	
		System.out.println("sum is :");
		add.printList(newHead);
		
		int num = add.listToInt(newHead);
		System.out.println(num);
	}
}

```
