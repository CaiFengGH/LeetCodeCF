```
package Medium;

/**
 * @author Ethan
 * @desc 寻找一个指定元素在已排序数组中的开始和结束索引 
 */
public class LC34_SearchRange {

	/**
	 * @author Ethan
	 * @desc 基于二分搜索查找范围
	 */
	public int[] searchRange(int[] nums,int target){
		int[] res = {-1,-1};
		int lo = 0,hi = nums.length - 1;
		
		while(nums[lo] < nums[hi]){
			int mid = lo + (hi - lo) / 2;
			if(nums[mid] > target){
				hi = mid - 1;
			}else if (nums[mid] < target){
				lo = mid + 1;
			}else{
				while(nums[lo--] == target){}
				while(nums[hi++] == target){}	
			}
		}
		
		if(nums[lo] == target && nums[hi] == target){
			res[0] = lo;
			res[1] = hi;
		}
		
		return res;
	}
}

```
