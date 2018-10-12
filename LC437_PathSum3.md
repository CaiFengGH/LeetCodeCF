```
package Easy;

/**
 * @author Ethan
 * @desc 返回二叉树中满足给定和的路径数量 
 * 路径不以头节点和尾节点开始及结束
 */
public class LC437_PathSum3 {

	public int pathSum(TreeNode root,int sum){
		if(root == null){
			return 0;
		}
		return pathSumFrom(root,sum) + pathSum(root.left,sum) + pathSum(root.right,sum);
	}

	/**
	 * @author Ethan
	 * @desc 从某个节点开始的路径和
	 */
	private int pathSumFrom(TreeNode root, int sum) {
		if(root == null){
			return 0;
		}
		return (root.value == sum ? 1 : 0) + 
				pathSumFrom(root.left,sum - root.value) 
				+ pathSumFrom(root.right,sum - root.value);
	}
	
	public static void main(String[] args) {
		LC437_PathSum3 ps = new LC437_PathSum3();
		
		//1-初始化树
		TreeNode a = new TreeNode(10);
		TreeNode b = new TreeNode(5);
		TreeNode c = new TreeNode(-3);
		TreeNode d = new TreeNode(3);
		TreeNode e = new TreeNode(2);
		TreeNode f = new TreeNode(11);
		TreeNode g = new TreeNode(3);
		TreeNode h = new TreeNode(-2);
		TreeNode i = new TreeNode(1);
		a.left = b;
		a.right = c;
		b.left = d;
		b.right = e;
		c.right = f;
		d.left = g;
		d.right = h;
		e.right = i;
		
		//2-验证数量
		int pathSum = ps.pathSum(a, 8);
		System.out.println(pathSum);
	}
}

```
