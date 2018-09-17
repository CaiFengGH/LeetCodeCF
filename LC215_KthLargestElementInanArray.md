```
package CaiFeng;

/**
 * @author Ethan
 */
public class LC215_KthLargestElementInanArray {
	
	public int findKthLargest(int[] nums,int k){
		int len = nums.length;
		int index = quickSelect(nums,0,len - 1,len - k + 1);
		return nums[index];
	}

	private int quickSelect(int[] nums, int lo, int hi, int k) {
		
		int i = lo;
		int j = hi;
		int init = nums[hi];
		
		while(i < j){
			if(nums[i++] > init){
				swap(nums,--i,--j);
			}
		}
		swap(nums,i,hi);
		
		int m = i - lo + 1;
		if(m == k){
			return i;
		}else if(m > k){
			return quickSelect(nums,lo,i - 1,k);
		}else{
			return quickSelect(nums, i+1, hi, k - m);
		}
	}

	private void swap(int[] nums, int i, int j) {
		int tmp = nums[i];
		nums[i] = nums[j];
		nums[j] = tmp;
	}
}

```
