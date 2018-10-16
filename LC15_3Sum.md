```
package Medium;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

/**
 * @author Ethan
 * @desc 返回满足三个数之和为0的所有组合 
 */
public class LC15_3Sum {

	public List<List<Integer>> sumWithZero(int[] nums){
		//1-异常参数检测
		if(nums == null || nums.length < 3){
			return null;
		}
		
		//2-初始化
		List<List<Integer>> res = new ArrayList<>();
		Arrays.sort(nums);
		
		//3-遍历
		for(int i = 0; i < nums.length - 2; i++){
			//4-确定第一个合适首位元素
			if(i == 0 || (i > 0 && nums[i] != nums[i-1])){
				int lo = i + 1,hi = nums.length - 1,sum = 0 - nums[i];
				while(lo < hi){
					//5-基于指针左右搜索剩余两位元素
					if(nums[lo] + nums[hi] == sum){
						res.add(Arrays.asList(nums[i],nums[lo],nums[hi]));
						//防止重复
						while(lo < hi && nums[lo] == nums[lo+1]){
							lo++;
						}
						while(lo < hi && nums[hi] == nums[hi - 1]){
							hi--;
						}
						lo++;
						hi--;
					}else if(nums[lo] + nums[hi] < sum){
						lo++;
					}else{
						hi--;
					}
				}
			}
		}
		return res;
	}
	
	public void printList(List<List<Integer>> ll){
		if(ll == null){
			return;
		}
		System.out.println("Sum is Zero:");
		for(List<Integer> l : ll){
			for(Integer i : l){
				System.out.print(i+" ");
			}
			System.out.println();
		}
	}
	
	public static void main(String[] args) {
		LC15_3Sum sum = new LC15_3Sum();
		int[] nums = {-1,0,1,2,-1,-4};
		List<List<Integer>> res = sum.sumWithZero(nums);
		sum.printList(res);
	}
	
}

```
