```
package Medium;

import java.util.ArrayList;
import java.util.List;

/**
 * @author Ethan
 * @desc 
 * return elements appear times more than n/3
 * input:1,1,1,3,3,2,2,2
 * output:1,2
 */
public class LC229_MajorityElementII {

	public List<Integer> majorityElement(int[] nums){
		//1-detect exception
		if(nums == null || nums.length < 0) return null;
		
		//2-initate
		List<Integer> res = new ArrayList<Integer>();
		int len = nums.length;
		int num1 = nums[0],num2 = nums[0];
		int count1 = 0,count2 = 0;
		
		//3-iterate
		for(int i = 0; i < len; i++){
			//4-Boyer-Moore Majority Vote Algorithm
			if(num1 == nums[i]){
				count1++;
			}else if(num2 == nums[i]){
				count2++;
			}else if(count1 == 0){
				num1 = nums[i];
				count1++;
			}else if(count2 == 0){
				num2 = nums[i];
				count2++;
			}else{
				count1--;
				count2--;
			}
		}
		
		//4-refresh count1: count2
		count1 = 0;
		count2 = 0;
		
		for(int i = 0; i < len; i++){
			if(nums[i] == num1) count1++;
			else if(nums[i] == num2) count2++;
		}
		
		//5-check length
		if(count1 > len / 3) res.add(num1);
		if(count2 > len / 3) res.add(num2);
		
		return res;
	}
	
	public void printList(List<Integer> l){
		if(l == null) return;
		for(Integer i : l){
			System.out.print(i +" ");
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC229_MajorityElementII me = new LC229_MajorityElementII(); 
		int[] nums = {1,1,1,3,3,2,2,2};
		List<Integer> res = me.majorityElement(nums);
		me.printList(res);
	}
}


```
