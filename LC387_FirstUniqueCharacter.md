```
package Easy;

import java.util.HashSet;
import java.util.LinkedHashMap;
import java.util.Set;

/**
 * @author Ethan
 * @desc 寻找字符串中第一个未重复出现的字符的索引 
 */
public class LC387_FirstUniqueCharacter {

	/**
	 * @author Ethan
	 * @desc 类似于桶排序的方式
	 */
	public int byTwoPass(String str){
		int[] freq = new int[256];
		
		for(int i = 0; i < str.length(); i++){
			freq[str.charAt(i)]++;
		}
		for(int j = 0; j < str.length(); j++){
			if(freq[str.charAt(j)] == 1){
				return j;
			}
		}
		return -1;
	}
	
	/**
	 * @author Ethan
	 * @desc linkedHashMap可以保持插入和访问顺序
	 */
	public int byLinkedHashMap(String str){
		LinkedHashMap<Character,Integer> lhm = 
				new LinkedHashMap<Character,Integer>(); 
		Set<Character> set = new HashSet<Character>();
		char c = ' ';
		
		for(int i = 0; i < str.length(); i++){
			c = str.charAt(i);
			if(set.contains(c)){
				if(lhm.get(c) != null){
					lhm.remove(c);
				}
			}else{
				lhm.put(c, i);
				set.add(c);
			}
		}
		return lhm.size() == 0 ? -1 : lhm.entrySet().iterator().next().getValue();
	}
}

```
