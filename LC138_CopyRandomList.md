```
package CaiFeng;

/**
 * @author Ethan
 * @desc 实现复杂链表的复制
 * http://yuanhsh.iteye.com/blog/2185974
 */
public class LC138_CopyRandomList {

	public Node copyRandomList(Node head){
		//1-异常参数检测
		if(head == null){
			return null;
		}
		//2-复制复杂链表节点，且将copy节点置于其后
		Node h = head;
		while(h != null){
			Node copy = new Node(h.value);
			Node next = h.next;
			h.next = copy;
			copy.next = next;
			h = next;
		}
		//3-复制复杂链表random节点
		h = head;
		while(h != null){
			if(h.random != null){
				h.next.random = h.random.next;
			}
			h = h.next.next;
		}
		//4-断开连接
		h = head;
		Node newHead = h.next;
		while(h != null){
			Node copy = h.next;
			h.next = copy.next;
			h = h.next;
			copy.next = h != null ? h.next : null;
		}
		//5-返回新链表头部
		return newHead;
	}
}

```
