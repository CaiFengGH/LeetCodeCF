```
package Easy;

import java.util.HashMap;
import java.util.Map;

/**
 * @author Ethan
 * @desc 判断字符串是否匹配给定模式串 
 */
public class LC290_WordPattern {

	/**
	 * @author Ethan
	 * @desc 利用put特性 
	 * key已经存在，返回旧值，新值覆盖旧值；key不存在，直接插入，返回null
	 */
	public boolean wordPattern(String str,String pattern){
		String[] strArr = str.split(" ");
		
		if(pattern.length() != strArr.length){
			return false;
		}
		
		Map<String,Integer> map = new HashMap<String,Integer>();
		for(int i = 0; i < strArr.length; i++){
			if(map.put(pattern.charAt(i)+"", i) != map.put(strArr[i], i)){
				return false;
			}
		}
		return true;
	}

	public static void main(String[] args) {
		LC290_WordPattern wp = new LC290_WordPattern();
		String pattern = "abba";
		String str = "dog cat cat dog";
		boolean res = wp.wordPattern(str, pattern);
		System.out.println(res);
	}
}
```
