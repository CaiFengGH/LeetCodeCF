```
package Easy;

import java.util.HashMap;
import java.util.Map;

/**
 * @author Ethan
 * @desc 判断是否一个数组中相距距离小于等于k的两个元素相等 
 */
public class LC219_ContainsDuplicateII {

	public boolean containsDuplicateII(int[] nums,int k){
		//1-异常情况检测
		if(nums == null || nums.length == 0){
			return false;
		}
		//2-初始化 map:
		Map<Integer,Integer> map = new HashMap<Integer,Integer>();
		//3-遍历
		for(int i = 0; i < nums.length; i++){
			if(map.containsKey(nums[i])){
				if(i - map.get(nums[i]) <= k){
					return true;
				}
			}
			map.put(nums[i], i);
		}
		return false;
	}
	
	public static void main(String[] args) {
		LC219_ContainsDuplicateII cd = new LC219_ContainsDuplicateII();
		int[] nums = {1,2,3,1,2,3};
		int k = 2;
		
		boolean res = cd.containsDuplicateII(nums, k);
		System.out.println(res);
	}
}

```
