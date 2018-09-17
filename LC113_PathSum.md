```
package CaiFeng;

import java.util.LinkedList;
import java.util.List;

/**
 * @author Ethan
 * @desc 返回二叉树满足一定sum的路径 
 * 链接：https://blog.csdn.net/derrantcm/article/details/47438073
 */
public class LC113_PathSum {

	//初始化成员变量 result:输出结果 l:路径结果 currSum:当前和
	private List<List<Integer>> result;
	private List<Integer> l;
	private int sum = 0;
	private int currSum = 0;
	
	public List<List<Integer>> pathSum(TreeNode root,int sum){
		result = new LinkedList<>();
		if(root != null){
			l = new LinkedList<Integer>();
			this.sum = sum;
			pathSum(root);
		}
		return result;
	}

	/**
	 * @author Ethan
	 * @desc 基于回溯法实现
	 */
	private void pathSum(TreeNode node) {
		if(node != null){
			//0-添加当前节点
			l.add(node.val);
			currSum += node.val;
			
			//1-叶子节点判断
			if(node.left == null && node.right == null && currSum == sum){
				//此时尤其需要添加，因为直接加l，l在回溯中会变动
				List<Integer> list = new LinkedList<Integer>();
				for(Integer i : l){
					list.add(i);
				}
				result.add(list);
			}
			
			//2-左子节点
			if(node.left != null){
				pathSum(node.left);
			}
			
			//3-右子节点
			if(node.right != null){
				pathSum(node.right);
			}

			//4-删除当前节点
			currSum -= node.val;
			l.remove(l.size() - 1);
		}
	}
}

```
