```
package CaiFeng;

import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;
import java.util.Queue;

/**
 * @author Ethan
 * @desc 广度遍历二叉树 
 */
public class LC107_BinaryTreeLevelOrderTraversalII {
	
	public List<List<Integer>> levelOrderBottom(TreeNode root) {
		List<List<Integer>> result = new ArrayList<>();
		if(root == null){
			return result;
		}
		List<Integer> list = null;
		int size = 0;
		
		Queue<TreeNode> queue = new LinkedList<>();
		queue.add(root);
		
		while(queue.size() > 0){
			list = new ArrayList<>();
			size = queue.size();
			for(int i = 0; i < size; i++){
				TreeNode tmp = queue.poll();
				list.add(tmp.val);
				if(tmp.left != null) queue.add(tmp.left);
				if(tmp.right != null) queue.add(tmp.right);
			}
			result.add(0, list);
		}
		
		return result;
	}
}

```
