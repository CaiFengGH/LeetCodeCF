```
package Easy;

import java.util.HashSet;

/**
 * @author Ethan
 * @desc 返回最长的回文串 
 */
public class LC409_LongestPalindrome {

	/**
	 * @author Ethan
	 * @desc 基于回文串的性质
	 */
	public int longestPalindrome(String s){
		//1-异常参数检测
		if(s.length() == 0 || s == null){
			return 0;
		}
		//2-初始化 set: count:
		HashSet<Character> set = new HashSet<Character>(); 
		int count = 0;
		char tmp = 0;
		
		//3-遍历s
		for(int i = 0; i < s.length(); i++){
			tmp = s.charAt(i);
			//增加和删除
			if(set.contains(tmp)){
				set.remove(tmp);
				count++;
			}else{
				set.add(tmp);
			}
		}
		//4-分情况返回
		return set.isEmpty() == true ? count * 2 : count * 2 + 1;
	}
	
	public static void main(String[] args) {
		LC409_LongestPalindrome lp = new LC409_LongestPalindrome();
		String s = "a";
		int maxLen = lp.longestPalindrome(s);
		System.out.println(maxLen);
	}
}

```
