```
package CaiFeng;

/**
 * @author Ethan
 */
public class LC105_ConstructBinaryTreefromPreorderandInorderTraversal {

	public TreeNode buildTree(int[] preorder, int[] inorder) {
        	return buildTree(inorder,0,inorder.length - 1,preorder,0);   
    	}

	public TreeNode buildTree(int[] inorder, int inStart, int inEnd, int[] preorder,
			int preStart) {
		if(preStart > preorder.length - 1 || inStart > inEnd){
			return null;
		}
		TreeNode root = new TreeNode(preorder[preStart]);
		int rIndex = 0;
		for(int i = inStart; i <= inEnd; i++){
			if(inorder[i] == root.val){
				rIndex = i;
				break;
			}
		}
		root.left = buildTree(inorder,inStart,rIndex - 1,preorder,preStart + 1);
		root.right = buildTree(inorder,rIndex + 1,inEnd,preorder,preStart + rIndex - inStart + 1);
		//5-杩斿洖root
		return root;
	}
}

```
