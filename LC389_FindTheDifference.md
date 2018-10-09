```
package Easy;

/**
 * @author Ethan
 * @desc 寻找新添加的字符 
 */
public class LC389_FindTheDifference {

	/**
	 * @author Ethan
	 * @desc 通过异或的方式寻找 
	 */
	public char findByXOR(String s,String t){
		//1-初始化长度
		int len = t.length();
		//2-初始化字符
		char c = t.charAt(len - 1); 
		//3-一次遍历
		for(int i = 0; i < len - 1; i++){
			c ^= s.charAt(i);
			c ^= t.charAt(i);
		}
		return c;
	}
	
	/**
	 * @author Ethan
	 * @desc 通过ascii码值和的差值 
	 */
	public char findBySum(String s,String t){
		//1-初始化asciiSumS: asciiSumT:
		int asciiSumS = 0;
		int asciiSumT = 0;
		
		//2-遍历
		for(int i = 0; i < s.length(); i++){
			asciiSumS += s.charAt(i);
			asciiSumT += t.charAt(i);
		}
		
		asciiSumT += t.charAt(t.length() - 1);
		
		return (char)(asciiSumT - asciiSumS);
	}
	
	public static void main(String[] args) {
		LC389_FindTheDifference diff = new LC389_FindTheDifference(); 
		
		String s = "abc";
		String t = "cbaa";
		
		char res = diff.findBySum(s, t);
		System.out.println(res);
	}
}

```
