```
package Medium;

import java.util.Arrays;
import java.util.Comparator;

/**
 * @author Ethan
 * @desc 
 * return maximum number represented as a string 
 * make up with int array
 */
public class LC179_LargestNumber {

	/**
	 * @author Ethan
	 * @desc 
	 * based on comparator
	 */
	public String largestNumber(int[] nums){
		//1-detect exception
		if(nums == null || nums.length == 0) return null;
		
		//2-initate strNums
		String[] strNums = new String[nums.length];
		for(int i = 0; i < nums.length;i++){
			strNums[i] = nums[i]+"";
		}
		
		//3-sort with comparator
		Arrays.sort(strNums, new Comparator<String>(){
			@Override
			public int compare(String s1, String s2) {
				return (s2 + s1).compareTo(s1 + s2);
			}
		});
		
		//4-attention case
		if(strNums[strNums.length - 1] == "0") return "0";
		
		//5-return
		String res = new String();
		for(String s : strNums){
			res += s;
		}
		return res;
	}
	
	public static void main(String[] args) {
		LC179_LargestNumber ln = new LC179_LargestNumber();
		int[] nums = {3,30,32,5,9};
		String res = ln.largestNumber(nums);
		System.out.println(res);
	}
}

```
