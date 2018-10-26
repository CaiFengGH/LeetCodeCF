```
package Medium;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

/**
 * @author Ethan
 * @desc 
 * input:
 * ["eat","tea","tan","ate","nat","bat"]
 * output:
 * [
 * 	["eat","tea","ate"],
 * 	["tan","nat"],
 * 	["bat"]
 * ]
 */
public class LC49_GroupAnagrams {

	/**
	 * @author Ethan
	 * @desc based on hashmap and arrays.sort
	 */
	public List<List<String>> groupAnagrams(String[] strs){
		//1-detect exception 
		if(strs == null || strs.length == 0) return null;
		
		//2-initate hashmap
		Map<String, List<String>> map = new HashMap<String,List<String>>();
		
		//3-iterate strs
		for(String str : strs){
			
			char[] chas = str.toCharArray();
			
			//4-arrays sort
			Arrays.sort(chas);
			String tmpStr = String.valueOf(chas);
//			System.out.println(tmpStr);
			
			//5-detect repeatable key
			if(!map.containsKey(tmpStr)){
				map.put(tmpStr, new ArrayList<String>());
			}
			map.get(tmpStr).add(str);
//			map.getOrDefault(tmpStr, new ArrayList<String>()).add(str);
		}
		
		//6-return
		return new ArrayList<List<String>>(map.values());
	}
	
	/**
	 * @author Ethan
	 * @desc 
	 */
	public void printList(List<List<String>> ll){
		if(ll == null) return;
		for(List<String> l : ll){
			for(String s : l){
				System.out.print(s + " ");
			}
			System.out.println();
		}
	}
	
	public static void main(String[] args) {
		LC49_GroupAnagrams ga = new LC49_GroupAnagrams();
		String[] strs = {"eat","tea","tan","ate","nat","bat"};
		List<List<String>> res = ga.groupAnagrams(strs);
		ga.printList(res);
	}
}

```
