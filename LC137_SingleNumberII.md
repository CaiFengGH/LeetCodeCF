```
package CaiFeng;

/**
 * @author Ethan
 * @desc 数组中每个元素出现过三次，仅有一个元素出现过一次，找到这个元素
 */
public class LC137_SingleNumberII {

	/**
	 * @author Ethan
	 * @desc 将数组中每个元素的每一位相加，和为3N或者3N+1，对3取模并保留此位 
	 */
	public int singleNumber(int[] nums){
		//1-初始化结果 res
		int res = 0;
		//2-遍历32位
		for(int i = 0; i < 32; i++){
			//3-初始化数量 count 掩码 mask
			int count = 0;
			int mask = 1<< i;
			//4-循环遍历数组
			for(int j = 0; j < nums.length; j++){
				//注意，此处相与后应该与mask值相等
				if((nums[j] & mask) == mask){
					count++;
				}
			}
			//5-count%3余1，则保留该位
			if(count % 3 == 1){
				res |= mask;
			}
		}
		return res;
	}
}

```
