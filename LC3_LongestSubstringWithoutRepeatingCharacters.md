```
package CaiFeng;

import java.util.HashMap;

/**
 * @author Ethan
 * @desc 返回字符串中无重复字符的最长子串
 */
public class LC3_LongestSubstringWithoutRepeatingCharacters {

	public int LongestSubstringWithoutRepeatingCharacters(String s){
		//1-异常参数检测
		if(s == null){
			return 0;
		}
		//2-初始化max
		int max = 0;
		HashMap<Character,Integer> hash = new HashMap<Character,Integer>();
		
		//3-循环移动快慢指针 i:快指针 j:慢指针
		for(int i = 0,j = 0; i < s.length(); i++){
			if(hash.containsKey(s.charAt(i))){
				//将j移动到该元素最新出现的右侧 和 目前的j比较 abba情况
				j = Math.max(j,hash.get(s.charAt(i)) + 1);
			}
			//所有元素均添加，且实时更新最新位置
			hash.put(s.charAt(i), i);
			//更新当前的max
			max = Math.max(max, i - j + 1);
		}
		return max;
	}
}

```
