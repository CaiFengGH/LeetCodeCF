```
package Easy;

/**
 * @author Ethan
 * @desc 判断字符串t是否是字符串s的一个anagram 
 */
public class LC242_ValidAnagram {

	/**
	 * @author Ethan
	 * @desc 基于桶思想
	 */
	public boolean isValidAnagram(String s,String t){
		//1-异常参数检测
		if(s.length() != t.length()){
			return false;
		}
		//2-初始化
		int[] charNum = new int[26];
		
		//3-遍历判断
		for(int i = 0; i < s.length(); i++){
			charNum[s.charAt(i) - 'a']++;
		}
		for(int j = 0; j < t.length(); j++){
			if(--charNum[t.charAt(j) - 'a'] < 0){
				return false;
			}
		}
		return true;
	}
	
	public static void main(String[] args) {
		LC242_ValidAnagram va = new LC242_ValidAnagram();
		
		String s = "rat";
		String t = "cat";
		
		boolean res = va.isValidAnagram(s, t);
		System.out.println(res);
	}
}

```
