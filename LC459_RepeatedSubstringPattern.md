```
package Easy;

/**
 * @author Ethan
 * @desc 返回一个字符串是否可以由一个字符串重复构成 
 * aba:true
 * abab:false
 */
public class LC459_RepeatedSubstringPattern {

	/**
	 * @author Ethan
	 * @desc 满足重复模式，必然可以整除某个数字
	 */
	public boolean repeatedSubstringByDivisor(String s){
		//1-初始化
		int len = s.length();
		//2-寻找除数
		for(int i = len / 2; i >= 1; i--){
			if(len % i == 0){
				int num = len / i;
				String batch = s.substring(0, i);
				StringBuffer sb = new StringBuffer();
				for(int j = 0; j < num;j++){
					sb.append(batch);
				}
				if(sb.toString().equals(s)){
					return true;
				}
			}
		}
		//3-构建字符串
		return false;
	}
	
	/**
	 * @author Ethan
	 * @desc 巧妙利用拼接方法
	 */
	public boolean repeatedSubstringByConcat(String s){
		String s2 = s + s;
		return s2.substring(1, s2.length() - 1).contains(s);
	}
	
	public static void main(String[] args) {
		LC459_RepeatedSubstringPattern rsp = new LC459_RepeatedSubstringPattern();
		String s = "abcabc";
		boolean isPattern = rsp.repeatedSubstringByConcat(s);
		System.out.println(isPattern);
	}
}

```
