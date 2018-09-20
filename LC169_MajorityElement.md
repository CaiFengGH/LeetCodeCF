```
package Easy;

/**
 * @author Ethan
 * @desc 返回数组中超过一半的元素 
 */
public class LC169_MajorityElement {

	public int moreThanHalf(int[] nums){
		//1-异常情况检测
		if(nums == null || nums.length == 0){
			return -1;
		}
		//2-初始化
		int element = nums[0];
		int times = 1;
		int count = 0;
		
		//3-遍历更新
		for(int i = 1; i < nums.length;i++){
			if(nums[i] == element){
				times++;
			}else{
				if(times == 0){
					element = nums[i];
					times = 1;
				}else{
					times--;
				}
			}
		}
		
		for(int j : nums){
			if(j == element){
				count++;
			}
		}
		
		return count > Math.floor(nums.length / 2) ? element : -1;
	}
	
	public static void main(String[] args) {
		LC169_MajorityElement me = new LC169_MajorityElement();
		int[] nums = {2,2,1,1,1,2};
		int element = me.moreThanHalf(nums);
		System.out.println(element);
	}
}

```
