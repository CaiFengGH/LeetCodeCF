```
package Medium;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

/**
 * @author Ethan
 * @desc 数组中有重复数字，且每个数字只能使用一次
 */
public class LC40_CombinationSum2 {

	public List<List<Integer>> combinationSum2(int[] nums,int target){
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
				if(i > start && nums[i] == nums[i - 1]) continue;
				tmpList.add(nums[i]);
				//加1表示数字不能被重复使用
				backtrack(res, tmpList, nums, remain - nums[i], i + 1);
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
		LC40_CombinationSum2 cs = new LC40_CombinationSum2();
		int target = 5;
		int[] nums = {2,5,2,1,2};
		List<List<Integer>> res = cs.combinationSum2(nums, target);
		cs.printList(res);
	}
}

```
