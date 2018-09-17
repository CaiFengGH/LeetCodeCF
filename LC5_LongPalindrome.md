```
package CaiFeng;

/**
 * @author Ethan
 * @desc 返回字符串中最大回文子串
 */
public class LC5_LongPalindrome {

	private int start;
	private int maxLen;
	
	public String longPalindrome(String s){
		//1-异常参数检测
		int len = s.length();
		if(len < 2){
			return s;
		}
		//2-循环遍历寻找最大回文子串
		for(int i = 0; i < len; i++){
			//回文串为奇数
			palindrome(s,i,i);
			//回文串为偶数
			palindrome(s,i,i+1);
		}
		return s.substring(start,start + maxLen);
	}

	private void palindrome(String s, int j, int k) {
		while(j >= 0 && k <= s.length()-1 && s.charAt(j) == s.charAt(k)){
			j--;
			k++;
		}
		if(maxLen < k - j - 1){
			start = j + 1;
			maxLen = k - j - 1;
		}
	}
}

```
