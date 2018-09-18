```
package Easy;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

/**
 * @author Ethan
 * @desc 数组正交，存在相同元素，相同元素个数以两者共同拥有的数量为准 
 */
public class LC350_IntersectArrayII {

	public int[] intersectArrayWithMap(int[] num1,int[] num2){
		//1-初始化 map: al:
		Map<Integer,Integer> map = new HashMap<Integer,Integer>();
		List<Integer> al = new ArrayList<Integer>();
		
		//2-遍历num1记录元素出现个数
		for(int i = 0; i < num1.length; i++){
			if(map.containsKey(num1[i])){
				map.put(num1[i], map.get(num1[i]) + 1);
			}else{
				map.put(num1[i], 1);
			}
		}
		
		//3-遍历num2添加元素
		for(int j = 0; j < num2.length; j++){
			if(map.containsKey(num2[j]) && map.get(num2[j]) > 0){
				al.add(num2[j]);
				map.put(num2[j], map.get(num2[j]) - 1);
			}
		}
		
		//4-初始化数组，赋值返回
		int[] res = new int[al.size()];
		int index = 0;
		for(int i : al){
			res[index++] = i;
		}
		return res;
	}
	
	public static void main(String[] args) {
		LC350_IntersectArrayII ia = new LC350_IntersectArrayII();
		int[] num1 = {1,2,2,1};
		int[] num2 = {2,2};
		
		int[] res = ia.intersectArrayWithMap(num1, num2);
		for(int i : res){
			System.out.println(i);
		}
	}
}
```
