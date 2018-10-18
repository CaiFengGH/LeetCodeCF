```
package Medium;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

/**
 * @author Ethan
 * @desc 数组中的数字没有重复，且每个数字可以重复使用
 * [2,3,6,7] 7
 * 7
 * 2,2,3
 */
public class LC39_CombinationSum {

	public List<List<Integer>> combinationSum(int[] nums,int target){
		List<List<Integer>> res = new ArrayList<List<Integer>>();
		Arrays.sort(nums);
		backtrack(res,new ArrayList<Integer>(),nums,target,0);
		return res;
	}

	private void backtrack(List<List<Integer>> res,
			ArrayList<Integer> tmpList, int[] nums, int remain, int start) {
		//依据remain大小做选择
		if(remain < 0) return;
		else if(remain == 0) res.add(new ArrayList<>(tmpList));
		else{
			for(int i = start; i < nums.length; i++){
				tmpList.add(nums[i]);
				backtrack(res, tmpList, nums, remain - nums[i], i);
				tmpList.remove(tmpList.size() - 1);
			}
		}
	}
	
	public void printList(List<List<Integer>> res){
		if(res == null){
			return;
		}
		for(List<Integer> l : res){
			for(Integer i : l){
				System.out.print(i);
			}
			System.out.println();
		}
	}
	
	public static void main(String[] args) {
		LC39_CombinationSum cs = new LC39_CombinationSum();
		int target = 7;
		int[] nums = {2,3};
		List<List<Integer>> res = cs.combinationSum(nums, target);
		cs.printList(res);
	}
	
}

```
