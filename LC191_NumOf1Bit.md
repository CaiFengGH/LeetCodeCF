```
package CaiFeng;

/**
 * @author Ethan
 * @desc 输出一个整型值的1比特数量 
 */
public class LC191_NumOf1Bit {

	/**
	 * @author Ethan
	 * @desc 利用掩码相与的思路
	 */
	public int hammingWeight(int num){
		//1-初始化 数量:count 掩码:mask
		int count =0;
		int mask = 1;
		for(int i = 0; i < 32; i++){
			if((num & mask) != 0){
				count++;
			}
			mask = mask << 1;
		}
		return count;
	}
}

```
