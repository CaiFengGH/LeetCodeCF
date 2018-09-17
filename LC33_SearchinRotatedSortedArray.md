```
package CaiFeng;

/**
 * @author Ethan
 */
public class LC33_SearchinRotatedSortedArray {
	 
	/**
	 * @author Ethan
	 */
	public int search(int[] nums, int target) {
		if(nums == null || nums.length == 0){
			return -1;
		}
		if(nums.length == 1){
			return nums[0] == target ? 0 : -1;
		}
		
		int start = 0;
		int end = nums.length - 1;
		int middle = 0;
		
		while(start < end){
			middle = (start + end) / 2;
			
			//1:1 2 3 4 5 6 7 2:3 4 5 6 7 1 2 3:5 6 7 1 2 3 4
			//1:1 2 3 4 5 6 2:3 4 5 6 1 2 3:4 5 6 1 2 3 4:5 6 1 2 3 4 
			if(target == nums[middle]){
				return middle;
			}
			
			if(nums[start] <= nums[middle]){
				if(target >= nums[start] && target < nums[middle]){
					end = middle - 1;
				}else{
					start = middle + 1;
				}
			}else{
				if(target > nums[middle] && target <= nums[end]){
					start = middle + 1;
				}else{
					end = middle - 1;
				}
			}
		}
		return nums[start] == target ? start : -1;
	}
}

```
