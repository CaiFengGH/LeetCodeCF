```
package CaiFeng;

/**
 * @author Ethan
 * @desc 删除有序单链表中重复的值
 */
public class LC83_RemoveDuplicatesfromSortedList {

	public ListNode removeDuplicatesfromSortedList(ListNode head){
		//1-异常参数检测
		if(head == null){
			return null;
		}
		//2-初始化当前节点
		ListNode curr = head; 
		//3-循环遍历
		while(curr!= null){
			//当前节点的next为空，break
			if(curr.next == null){
				break;
			}
			//当前节点与next节点的值相等，删除节点；不等，移动当前节点
			if(curr.val == curr.next.val){
				curr.next = curr.next.next;
			}else{
				curr = curr.next;
			}
		}
		return head;
	}
}

```
