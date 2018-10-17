```
package Medium;

import java.util.ArrayList;
import java.util.List;

/**
 * @author Ethan
 * @desc 生成括号对 
 */
public class LC22_GenerateParenthesis {

	/**
	 * @author Ethan
	 * @desc 基于DFS遍历调用
	 */
	public List<String> generateParenthesis(int n){
		List<String> al = new ArrayList<String>();
		generateOne("",al,n,n);
		return al;
	}

	/**
	 * @author Ethan
	 * @desc 生成一对括号 
	 */
	private void generateOne(String str, List<String> al, int left, int right) {
		//保证左括号数量多于右括号
		if(left > right){
			return;
		}
		if(left > 0){
			generateOne(str+"(", al, left - 1, right);
		}
		if(right > 0){
			generateOne(str+")", al, left, right - 1);
		}
		if(left == 0 && right == 0){
			al.add(str);
			return;
		}
	}
	
	public void printList(List<String> al){
		for(String str : al){
			System.out.println(str);
		}
	}
	
	public static void main(String[] args) {
		LC22_GenerateParenthesis gp = new LC22_GenerateParenthesis();
		int n = 3;
		List<String> res = gp.generateParenthesis(n);
		gp.printList(res);
	}
}

```
