```
package Easy;

import java.util.HashMap;
import java.util.Map;

/**
 * @author Ethan
 * @desc 判断两个字符串是否是同型字符串 
 */
public class LC205_IsomorphicStrings {
	
	/**
	 * @author Ethan
	 * @desc 基于map的put方法
	 */
	public boolean isomorphicStringsByMap(String s,String t){
		//1-异常参数检测
		if(s.length() != t.length()){
			return false;
		}
		//2-初始化
		Map<Character,Integer> mapS = new HashMap<Character,Integer>();
		Map<Character,Integer> mapT = new HashMap<Character,Integer>();
		
		//3-遍历字符串
		for(int i = 0; i < s.length(); i++){
			if(mapS.put(s.charAt(i), i) != mapT.put(t.charAt(i), i)){
				return false;
			}
		}
		return true;
	}
	
	public static void main(String[] args) {
		LC205_IsomorphicStrings is = new LC205_IsomorphicStrings();
		String s = "paper";
		String t = "title";
		boolean res = is.isomorphicStringsByMap(s, t);
		System.out.println(s + " and " + t + " is "+ 
				(res == true ? "isomorphic" :"unisomorphic"));
	}
}
```
