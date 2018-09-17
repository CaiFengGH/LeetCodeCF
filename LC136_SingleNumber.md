```
package CaiFeng;

/**
 * @author Ethan
 */
public class LC136_SingleNumber {

	/**
	 * @author Ethan
	 * @desc 寮傛垨鎬ц川: a ^ b = b ^ a, 0 ^ a = a, a ^ a = 0
	 */
	public int singlenNumber(int[] nums){
		int element = 0;
		for(int i = 0; i < nums.length; i++){
			element = element ^ nums[i];
		}
		return element;
	}
}

```
