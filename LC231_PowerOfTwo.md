```
package Easy;

/**
 * @author Ethan
 * @desc 判断一个数是否是2的幂次方 
 */
public class LC231_PowerOfTwo {

	public boolean isPowerOfTwoByBitOperation(int num){
		//int型最小值-2147483648的二进制表示也是一个比特位为1
		return num > 0 && (num & (num - 1)) == 0;
	}
	
	public boolean isPowerOfTwoByBitCount(int num){
		return num > 0 && Integer.bitCount(num) == 1;
	}

	public static void main(String[] args) {
		LC231_PowerOfTwo pot = new LC231_PowerOfTwo();
		int num = 3;
		boolean res = pot.isPowerOfTwoByBitCount(num);
		System.out.println("BitCount:" + res);

		res = pot.isPowerOfTwoByBitOperation(num);
		System.out.println("BitOperation:" + res);
		
	}
}

```
