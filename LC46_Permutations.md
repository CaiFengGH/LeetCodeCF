```
package Medium;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

/**
 * @author Ethan
 * @desc 返回数组的全排列 
 * input:
 * [1,2,3]
 * output:
 * [1,2,3] [1,3,2] [2,1,3] [2,1,4] [3,1,2] [3,2,1]
 */
public class LC46_Permutations {

	public List<List<Integer>> permute(int[] nums){
		List<List<Integer>> res = new ArrayList<List<Integer>>();
		Arrays.sort(nums);
		backTrack(res,new ArrayList<Integer>(),nums);
		return res;
	}

	private void backTrack(List<List<Integer>> res,
			ArrayList<Integer> tmpList, int[] nums) {
		if(tmpList.size() == nums.length){
			res.add(new ArrayList<>(tmpList));
		}else{
			for(int i = 0; i < nums.length;i++){
				if(tmpList.contains(nums[i])) continue;
				tmpList.add(nums[i]);
				backTrack(res, tmpList, nums);
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
		LC46_Permutations p = new LC46_Permutations();
		int[] nums = {1,2,3};
		List<List<Integer>> res = p.permute(nums);
		p.printList(res);
	}
}

```
