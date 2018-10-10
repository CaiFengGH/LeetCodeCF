```
package Easy;

import java.util.Stack;

/**
 * @author Ethan
 * @desc 计算树的左叶子之和
 *     1 
 *   2   3
 *  4     5
 *  返回4 
 */
public class LC404_SumOfLeftLeaves {

	/**
	 * @author Ethan
	 * @desc 基于递归 
	 */
	public int sumOfLeftLeavesByRecursive(TreeNode root){
		//1-异常情况监测
		if(root == null){
			return 0;
		}
		//2-初始化
		int sum = 0;
		//3-左右子树判断
		if(root.left != null){
			if(root.left.left == null && root.left.right == null){
				sum += root.left.value;
			}else{
				sum += sumOfLeftLeavesByRecursive(root.left);
			}
		}
		sum += sumOfLeftLeavesByRecursive(root.right);
		//4-返回
		return sum;
	}
	
	/**
	 * @author Ethan
	 * @desc 基于迭代
	 */
	public int sumOfLeftLeavesByIterative(TreeNode root){
		//1-异常情况监测
		if(root == null){
			return 0;
		}
		//2-初始化 sum: stack:
		int sum = 0;
		Stack<TreeNode> stack = new Stack<TreeNode>();
		stack.push(root);
		TreeNode tmp = null;
		
		//3-压栈和求和
		while(!stack.isEmpty()){
			tmp = stack.pop();
			//4-左节点：是否是叶子节点判断
			if(tmp.left != null){
				if(tmp.left.left == null && tmp.left.right == null){
					sum += tmp.left.value;
				}else{
					stack.push(tmp.left);
				}
			}
			//5-右节点：是否为空
			if(tmp.right != null){
				if(tmp.right.left != null || tmp.right.right != null){
					stack.push(tmp.right);
				}
			}
		}
		//6-返回结果
		return sum;
	}
	
	public static void main(String[] args) {
		LC404_SumOfLeftLeaves soll = new LC404_SumOfLeftLeaves();
		
		TreeNode a = new TreeNode(1);
		TreeNode b = new TreeNode(2);
		TreeNode c = new TreeNode(3);
		TreeNode d = new TreeNode(4);
		TreeNode e = new TreeNode(5);
		
		a.left = b;
		a.right = c;
		b.left = d;
		c.right = e;
		
		int sum = soll.sumOfLeftLeavesByIterative(a);
		System.out.println(sum);
	}
}
```
