```
package Easy;

/**
 * @author Ethan
 * @desc 基于前后双指针实现反转
 */
public class LC344_ReverseString {

	public String reverseString(String str){
		//1-异常参数检测
		if(str == null || str.length() == 0){
			return str;
		}
		//2-初始化 chas: left: right:
		char[] chas = str.toCharArray();
		int left = 0;
		int right = chas.length - 1;
		char tmp = ' ';
		//3-移动指针
		while(left < right){
			tmp = chas[left];
			chas[left] = chas[right];
			chas[right] = tmp;
			left++;
			right--;
		}
		return String.valueOf(chas);
	}
	
	public static void main(String[] args) {
		LC344_ReverseString rs = new LC344_ReverseString();
		String str = "A man, a plan, a canal: Panama";
		String res = rs.reverseString(str);
		System.out.println(str+"-"+res);
	}
}

```
