```
package Easy;

/**
 * @author Ethan
 * @desc 求解数组给定索引范围内之和 
 */
public class LC304_NumArray {

	//sum[i]表示i之前不包含i的num中的和
	public int[] sum;
	
	public LC304_NumArray(int[] nums){
		sum = new int[nums.length + 1];
		for(int i = 0; i < nums.length; i++){
			sum[i + 1] = sum[i] + nums[i];
		}
	}
	
	/**
	 * @author Ethan
	 * @desc 利用片段和
	 */
	public int sumRange(int i,int j){
		return sum[j + 1] - sum[i];
	}
}
```
