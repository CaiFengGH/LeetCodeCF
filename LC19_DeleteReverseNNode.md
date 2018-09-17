```
package CaiFeng;

/**
 * @author Ethan
 * @desc 删除倒数第n个节点
 */
public class LC19_DeleteReverseNNode {
	
	/**
	 * @author Ethan
	 * @desc 基于前后指针，在一次遍历前提下删除倒数n节点 
	 */
	public Node deleteReverseNNode(Node head,int n){
		//1-初始化demy节点，指向头节点
		Node demy = new Node(0);
		demy.next = head;
		//2-初始化fast和slow指针为demy
		Node fast = demy;
		Node slow = demy;
		//3-fast指针前进n+1步
		for(int i = 1; i <= n + 1; i++){
			fast = fast.next;
		}
		//4-fast和slow共同前进，如果节点数恰好为n个，此处不循环
		while(fast != null){
			fast = fast.next;
			slow = slow.next;
		}
		//5-移除倒数n节点
		slow.next = slow.next.next;
		return demy.next;
	}
}
```
