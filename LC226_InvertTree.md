```
package CaiFeng;

import java.util.LinkedList;
import java.util.Queue;

/**
 * @author Ethan
 * @desc 实现二叉树的反转 
 */
public class LC226_InvertTree {
	
	/**
	 * @author Ethan
	 * @desc 基于递归的方式 
	 */
	public TreeNode invertTree(TreeNode root){
		//1-递归结束条件
		if(root == null){
			return null;
		}
		//2-当前节点左右子树反转
		TreeNode right = invertTree(root.right);
		TreeNode left = invertTree(root.left);
		
		//3-更新当前节点的左右子树
		root.left = right;
		root.right = left;
		
		return root;
	}
	
	/**
	 * @author Ethan
	 * @desc 对于每个节点更改左右子树
	 */
	public TreeNode invertTree2(TreeNode root){
		//1-初始化 queue:有序 存储每层节点
		Queue<TreeNode> queue = new LinkedList<TreeNode>();
		queue.add(root);
		//2-循环遍历queue，直到其大小为0
		while(queue.size() > 0){
			//弹出节点
			TreeNode curr = queue.poll();
			//更改其左右子节点
			TreeNode tmp = curr.left;
			curr.left = curr.right;
			curr.right = tmp;
			//将下一层节点进行添加
			if(curr.left != null) queue.add(curr.left);
			if(curr.right != null) queue.add(curr.right);
		}
		//3-返回root节点
		return null;
	}
}
```
