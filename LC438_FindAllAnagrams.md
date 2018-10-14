```
package Easy;

import java.util.HashMap;
import java.util.LinkedList;
import java.util.List;
import java.util.Map;

/**
 * @author Ethan
 * @desc 
 * s:"cbaebabacd" p:"abc"
 */
public class LC438_FindAllAnagrams {

	/**
	 * @author Ethan
	 * @desc 基于滑动窗口算法
	 */
	public List<Integer> findAnagrams(String s,String p){
		//1-初始化 res:
		List<Integer> res = new LinkedList<>(); 
		if(p.length() > s.length()){
			return res;
		}
		
		//2-初始化 map:
		Map<Character,Integer> map = new HashMap<>();
		for(int i = 0; i < p.length(); i++){
			map.put(p.charAt(i), map.getOrDefault(p.charAt(i), 0) + 1);
		}
		
		//3-初始化 end: begin: counter:
		int counter = map.size();
		int begin = 0;
		int end = 0;
		
		//4-遍历s
		while(end < s.length()){
			//map值减
			char tmp = s.charAt(end);
			if(map.containsKey(tmp)){
				map.put(tmp, map.get(tmp) - 1);
				if(map.get(tmp) == 0){
					counter--;
				}
			}
			end++;
			
			//map值加
			while(counter == 0){
				char tmp2 = s.charAt(begin);
				if(map.containsKey(tmp2)){
					map.put(tmp2,map.get(tmp2) + 1);
					if(map.get(tmp2) > 0){
						counter++;
					}
				}
				if(end - begin == p.length()){
					res.add(begin);
				}
				begin++;
			}
		}
		return res;
	} 

	public void printList(List<Integer> res) {
		for(int i : res){
			System.out.print(i+"_");	
		}
		System.out.println();
	}

	public static void main(String[] args) {
		LC438_FindAllAnagrams faa = new LC438_FindAllAnagrams();
		String s = "abab";
		String p = "ab";
		List<Integer> res = faa.findAnagrams(s, p);
		faa.printList(res);
	}
}

```
