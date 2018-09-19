```
package Easy;

/**
 * @author Ethan
 * @desc 在二叉搜索树中，返回两个树节点的最低公共祖先 
 */
public class LC235_LowestCommonAncestor {

	/**
	 * @author Ethan
	 * @desc  
	 * 1-p或q分布在root左右子树中，或者其中一个为root，则最低根节点为root 此时乘积小于0
	 * 2-判断位于哪个子树中
	 */
	public TreeNode lowestCommonAncestor(TreeNode root,TreeNode p,TreeNode q){
		return (root.value - p.value) * (root.value - q.value) <= 0 
				? root : lowestCommonAncestor((p.value < root.value
						? root.left : root.right ), p, q);
	}
}
```
