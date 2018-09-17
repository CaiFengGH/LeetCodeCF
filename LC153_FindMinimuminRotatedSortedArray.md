```
package CaiFeng;

/**
 * @author Ethan
 */
public class LC153_FindMinimuminRotatedSortedArray {
	
	/**
	 * @author Ethan
	 */
	public int findMin(int[] nums) {
		if(nums == null || nums.length == 0){
			return -1;
		}
		if(nums.length == 1){
			return nums[0];
		}
		
		int start = 0;
		int end = nums.length - 1;
		int middle = 0;
		
		//濂囨暟涓� 1:1 2 3 4 5 6 7 2:3 4 5 6 7 1 2 3:5 6 7 1 2 3 4
		//鍋舵暟涓� 1:1 2 3 4 5 6 2:3 4 5 6 1 2 3:4 5 6 1 2 3 4:5 6 1 2 3 4 
		while(start < end){
			middle = (start + end) / 2;
			if(middle > 0 && nums[middle] < nums[middle - 1]){
				return nums[middle];
			}
			if(nums[start] <= nums[middle] && nums[middle] > nums[end]){
				start = middle + 1;
			}else{
				end = middle - 1;
			}
		}
		return nums[start];
	}
}

```
