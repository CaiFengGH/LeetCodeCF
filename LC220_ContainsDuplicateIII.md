```
package Medium;

import java.util.HashMap;
import java.util.Map;

/**
 * @author Ethan
 * @desc 
 * absolute difference between i,j at most k and num[i],num[j] at most t
 * input:
 * 1,2,3,1 k = 3,t = 0
 * output:
 * true
 */
public class LC220_ContainsDuplicateIII {

	public boolean containsDuplicate(int[] nums,int k,int t){
		//1-detect exception
		if(t < 0) return false;
		
		//2-initate
		Map<Integer,Integer> buckets = new HashMap<Integer,Integer>();
		int width = t + 1;
		
		
		//3-iterate
		for(int i = 0; i < nums.length;i++){
			//4-get bucket index
			int index = getIndex(nums[i],width);

			if(buckets.containsKey(index)){
				return true;
			}
			if(buckets.containsKey(index - 1) && Math.abs(buckets.get(index - 1)- nums[i]) < width){
				return true;
			}
			if(buckets.containsKey(index + 1) && Math.abs(buckets.get(index + 1)- nums[i]) < width){
				return true;
			}
			
			buckets.put(index, nums[i]);
			//5-greater than k keep window size
			if(i >= k){
				buckets.remove(getIndex(nums[i - k],width));
			}
		}
		return false;
	}

	private int getIndex(int i, int width) {
		return i < 0 ? i - 1/width -1 : i / width;
	}

	public static void main(String[] args) {
		LC220_ContainsDuplicateIII cd = new LC220_ContainsDuplicateIII();
		int[] nums = {1,2,3,1};
		int k = 3;
		int t = 0;
		boolean isContain = cd.containsDuplicate(nums, k, t);
		System.out.println(isContain);
	}
}



```
