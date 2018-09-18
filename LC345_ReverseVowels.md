```
package Easy;

/**
 * @author Ethan
 * @desc 反转字符串中的元音字母 
 */
public class LC345_ReverseVowels {

	/**
	 * @author Ethan
	 * @desc 基于双指针移动方式
	 */
	public String reverseVowels(String str){
		//1-异常参数检测
		if(str == null || str.length() == 0){
			return str;
		}
		//2-初始化 vowels: start: end:
		String vowels = "aeiouAEIOU";
		
		char[] chas = str.toCharArray();
		int start = 0;
		int end = chas.length - 1;
		char tmp = ' ';
		
		//3-基于左右指针移动置换元素
		while(start < end){
			//从左往右遍历元音字母
			while(start < end && !vowels.contains(chas[start]+"")){
				start++;
			}
			//从右往左遍历元音字母
			while(start < end && !vowels.contains(chas[end]+"")){
				end--;
			}
			//交换
			tmp = chas[start];
			chas[start] = chas[end];
			chas[end] = tmp;
			start++;
			end--;
		}
		return String.valueOf(chas);
	}
	
	public static void main(String[] args) {
		LC345_ReverseVowels rv = new LC345_ReverseVowels();
		String str = "leetcode";
		String res = rv.reverseVowels(str);
		System.out.println(res);
	}
}
```
