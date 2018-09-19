```
package Easy;

import java.util.HashSet;
import java.util.Set;

/**
 * @author Ethan
 * @desc 判断一个数组中是否包含重复值 
 */
public class LC217_ContainsDuplicate {

	/**
	 * @author Ethan
	 * @desc 基于HashSet实现 
	 */
	public boolean containsDuplicate(int[] nums){
		//1-异常参数检测
		if(nums == null || nums.length == 0){
			return false;
		}
		//2-初始化 set
		Set<Integer> set = new HashSet<Integer>();
		//3-遍历
		for(int i : nums){
			if(set.contains(i)){
				return true;
			}
			set.add(i);
		}
		return false;
	}	
}

```
