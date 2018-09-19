```
package Easy;

import java.util.ArrayList;
import java.util.List;
import java.util.Stack;

/**
 * @author Ethan
 * @desc 二叉树路径 
 */
public class LC257_BinaryTreePaths {

	/**
	 * @author Ethan
	 * @desc 基于栈的深度优先遍历
	 */
	public List<String> binaryTreePaths(TreeNode root){
		
		List<String> list = new ArrayList<String>();
		Stack<TreeNode> stackNode = new Stack<TreeNode>();
		Stack<String> stackStr = new Stack<String>();
	
		stackNode.push(root);
		stackStr.push("");
		
		TreeNode curNode = null;
		String curStr = "";
		
		while(!stackNode.isEmpty()){
			curNode = stackNode.pop();
			curStr = stackStr.pop();
			
			if(curNode.left == null && curNode.right == null){
				list.add(curStr+curNode.value);
			}
			
			if(curNode.left != null){
				stackNode.push(curNode.left);
				stackStr.push(curStr+curNode.value+"->");
			}
			if(curNode.right != null){
				stackNode.push(curNode.right);
				stackStr.push(curStr+curNode.value+"->");
			}
		}
		
		return list;
	}
	
	public static void main(String[] args) {
		LC257_BinaryTreePaths btp = new LC257_BinaryTreePaths();
		TreeNode a = new TreeNode(1);
		TreeNode b = new TreeNode(2);
		TreeNode c = new TreeNode(3);
		TreeNode d = new TreeNode(4);
		
		a.left = b;
		a.right = c;
		b.right = d;
		
		List<String> list = btp.binaryTreePaths(a);
		for(String s : list){
			System.out.println(s);
		}
	}
}
```
