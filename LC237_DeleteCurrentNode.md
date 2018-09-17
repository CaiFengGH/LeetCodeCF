```
package CaiFeng;

/**
 * @author Ethan
 * @desc 未给定链表头节点，直接删除当前节点 
 */
public class LC237_DeleteCurrentNode {

	public void deleteCurrentNode(Node curr){
		//1-当前节点的下一个节点的值覆盖当前节点
		curr.value = curr.next.value;
		//2-删除当前节点的下一个节点
		curr.next = curr.next.next;
	}
	
	
}

```
