```
package CaiFeng;

/**
 * @author Ethan
 * @desc 实现字符串中逆序排列
 */
public class LC151_ReverseWordInString {

	/**
	 * @author Ethan
	 * @desc 基于数组存储的方式
	 */
	public String reverseWordInString(String str){
		
		String[] strArr = str.split(" +");
		int len = strArr.length;
		int index = len - 1;
		String res = "";
		
		if(len == 1){
			return strArr[0];
		}
		
		for(; index >= 0; index--){
			res += strArr[index] + " ";
		}
		return res.trim();
	}
}

```
