```
package Easy;

/**
 * @author Ethan
 * @desc 将数组中的0全部移动到数组末尾
 */
public class LC283_MoveZeros {

	/**
	 * @author Ethan
	 * @desc 基于移动插入的思想
	 */
	public void moveZeros(int[] nums){
		int index = 0; 
		
		for(int i : nums){
			if(i != 0){
				nums[index++] = i;
			}
		}

		while(index < nums.length){
			nums[index++] = 0;
		}
	}
	
	public void printArr(int[] nums){
		for(int i : nums){
			System.out.print(i + "->");
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC283_MoveZeros mz = new LC283_MoveZeros();
		int[] nums = {0,1,0,3,12};
		mz.printArr(nums);
		mz.moveZeros(nums);
		mz.printArr(nums);
	}
}

```
