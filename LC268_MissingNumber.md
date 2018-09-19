```
package Easy;

import java.util.Arrays;

/**
 * @author Ethan
 * @desc 寻找缺失的数字 
 */
public class LC268_MissingNumber {

	/**
	 * @author Ethan
	 * @desc 
	 */
	public int missingNumber(int[] nums){
		//1-排序
		Arrays.sort(nums);
		if(nums[0] == 1){
			return 0;
		}
		if(nums[nums.length - 1] == nums.length - 1){
			return nums.length;
		}
		//2-遍历寻找差值
		for(int i = 0; i < nums.length - 1; i++){
			if(nums[i + 1] != nums[i] + 1){
				return nums[i] + 1;
			}
		}
		return -1;
	}
	
	public static void main(String[] args) {
		LC268_MissingNumber mn = new LC268_MissingNumber();
		int[] nums = {9,6,4,2,3,5,7,0,1};
		int res = mn.missingNumber(nums);
		System.out.println(res);
	}
}
```
