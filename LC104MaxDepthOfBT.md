```
package Easy;

import java.util.LinkedList;
import java.util.Queue;

/**
 * @author Ethan
 * @desc 返回二叉树的最大深度
 */
public class LC104MaxDepthOfBT {

	/**
	 * @author Ethan
	 * @desc 基于递归思路
	 */
	public int maxDepthByRecursive(TreeNode root){
		return root == null ? 0 : 1 + Math.max(maxDepthByRecursive(root.left), 
				maxDepthByRecursive(root.right));
	}
	
	/**
	 * @author Ethan
	 * @desc 基于广度优先遍历思路
	 */
	public int maxPathByBPS(TreeNode root){
		Queue<TreeNode> queue = new LinkedList<TreeNode>();
		if(root == null){
			return 0;
		}
		int depth = 1;
		int size = 0;
		queue.offer(root);
		
		while(!queue.isEmpty()){
			size = queue.size();
			for(int i = 0; i < size; i++){
				root = queue.poll();
				if(root.left != null){
					queue.add(root.left);
				}
				if(root.right != null){
					queue.add(root.right);
				}
			}
			if(queue.isEmpty()){
				break;
			}
			depth++;
		}
		return depth;
	}
	
	public static void main(String[] args) {
		LC104MaxDepthOfBT maxDepth = new LC104MaxDepthOfBT();
		
		TreeNode a = new TreeNode(3);
		TreeNode b = new TreeNode(9);
		TreeNode c = new TreeNode(20);
		TreeNode d = new TreeNode(15);
		TreeNode e = new TreeNode(7);

		a.left = b;
		a.right = c;
		c.left = d;
		c.right = e;
	
		int max = maxDepth.maxDepthByRecursive(a);
		System.out.println(max);
		
		max = maxDepth.maxPathByBPS(a);
		System.out.println(max);
	
	}
}
```
