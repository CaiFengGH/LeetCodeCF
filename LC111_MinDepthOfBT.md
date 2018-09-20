```
package Easy;

import java.util.LinkedList;
import java.util.Queue;

/**
 * @author Ethan
 * @desc 返回二叉树的最小深度 
 */
public class LC111_MinDepthOfBT {

	/**
	 * @author Ethan
	 * @desc 基于广度优先遍历
	 */
	public int minPathByBPS(TreeNode root){
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
				if(root.left == null && root.right == null){
					return depth;
				}
				if(root.left != null){
					queue.add(root.left);
				}
				if(root.right != null){
					queue.add(root.right);
				}
			}
			depth++;
		}
		return depth;
	}
	
	/**
	 * @author Ethan
	 * @desc 基于递归实现 
	 */
	public int minPathByRecursive(TreeNode root){
		//1-递归结束条件
		if(root == null){
			return 0;
		}
		//2-左右子树
		int left = minPathByRecursive(root.left);
		int right = minPathByRecursive(root.right);
		
		return (left == 0 || right == 0) ? left + right + 1 : Math.min(left, right) + 1;
	}
}

```
