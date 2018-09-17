```
package CaiFeng;

/**
 * @author Ethan
 */
public class LC106_ConstructBinaryTreefromInorderandPostorderTraversal {

	public TreeNode buildTree(int[] inorder,int[] postorder){
		return buildTree(inorder,0,inorder.length - 1,postorder,postorder.length - 1);
	}

	/**
	 * @author Ethan
	 */
	public TreeNode buildTree(int[] inorder, int inStart, int inEnd, int[] postorder,
			int postStart) {
		if(inStart > inEnd || postStart < 0){
			return null;
		}
		TreeNode root = new TreeNode(postorder[postStart]);
		int rIndex = 0;
		for(int i = inStart; i >= inEnd; i--){
			if(inorder[i] == root.val){
				rIndex = i;
				break;
			}
		}
		root.right = buildTree(inorder,rIndex + 1,inEnd,postorder,postStart - 1);
		root.left = buildTree(inorder,inStart,rIndex - 1,postorder,postStart - (rIndex - inStart) - 1);
		//5-杩斿洖鏍硅妭鐐�
		return root;
	}
}

```
