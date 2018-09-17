```
package CaiFeng;

/**
 * @author Ethan
 * @desc 数组中每个元素均出现两次，仅有两个元素出现一次，找出这两个元素 
 */
public class LC260_SimpleNumberIII {

	/**
	 * @author Ethan
	 * @desc 所有元素异或，结尾为出现一次的两个元素异或的结果a，对a取补码后相与，找出分类两者的特征 
	 * @note https://blog.csdn.net/yeruby/article/details/49853385
	 */
	public int[] simpleNumber(int[] nums){
		//1-初始化出现一次的两个元素异或结果 diff 输出结果 ans
		int diff = 0;
		int[] ans = new int[2];
		//2-对所有元素进行异或
		for(int num : nums){
			diff = diff ^ num;
		}
		//3-寻找区分两个元素的特征，与其补码进行异或
		diff &= -diff;
		for(int num : nums){
			if((num & diff) == 0){
				ans[0] ^= num;
			}else{
				ans[1] ^= num;
			}
		}
		return ans;
	}
}
```
