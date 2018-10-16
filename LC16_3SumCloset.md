```
package Medium;

import java.util.Arrays;

/**
 * @author Ethan
 * @desc 返回三个数之和最接近target的和 
 */
public class LC16_3SumCloset {

	/**
	 * @author Ethan
	 * @desc 基于类似于3sum的方法
	 */
	public int sumCloset(int[] nums,int target){
		//1-异常参数检测
		if(nums == null || nums.length < 3){
			return -1;
		}
		
		//2-初始化 res
		Arrays.sort(nums);
		int res = nums[0] + nums[1] + nums[nums.length - 1];
		
		//3-遍历 注意边界
		for(int i = 0; i < nums.length - 2; i++){
			int lo = i + 1,hi = nums.length - 1;
			while(lo < hi){
				int sum = nums[i] + nums[lo] + nums[hi];
				if(sum > target){
					hi--;
				}else if(sum < target){
					lo++;
				}else{
					return sum;
				}
				//4-更新结果
				if(Math.abs(sum - target) < Math.abs(res - target)){
					res = sum;
				}
			}
		}
		
		//5-返回结果
		return res;
	}
	
	public static void main(String[] args) {
		LC16_3SumCloset sumCloset = new LC16_3SumCloset();
		int[] nums = {-1,2,1,-4};
		int target = 1;
		int res = sumCloset.sumCloset(nums, target);
		System.out.println(res);
	}
}

```
