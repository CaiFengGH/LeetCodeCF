```
package Easy;

/**
 * @author Ethan
 * @desc 旋转数组 
 */
public class LC189_RotateArray {

	/**
	 * @author Ethan
	 * @desc 基于三次反转实现数组旋转 
	 */
	public void rotateArray(int[] nums,int k){
		//1-异常参数检测
		if(nums == null || nums.length == 0 || nums.length < k){
			return ;
		}
		
		int len = nums.length;
		//2-三次反转
		reverse(nums,0,len - k - 1);
		reverse(nums,len - k,len - 1);
		reverse(nums,0,len - 1);
	}

	/**
	 * @author Ethan
	 * @desc 基于双指针实现反转
	 */
	private void reverse(int[] nums, int i, int j) {
		int tmp = 0;
		while(i < j){
			tmp = nums[j];
			nums[j] = nums[i];
			nums[i] = tmp;
			i++;
			j--;
		}
	}

	public void printArr(int[] nums){
		for(int i : nums){
			System.out.print(i);
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC189_RotateArray ra = new LC189_RotateArray();
		int[] nums = {1,2,3,4,5,6,7};
		
		ra.printArr(nums);
		ra.rotateArray(nums, 3);
		ra.printArr(nums);
	}
}

```
