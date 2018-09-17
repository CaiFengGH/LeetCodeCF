```
package CaiFeng;

/**
 * @author Ethan
 */
public class LC66_PlusOne {
	public int[] plusOne(int[] digits){
		//大数相加过程
		int len = digits.length;
		for(int i = len - 1; i >= 0; i--){
			//低位为9，直接赋值为0，不为9，加1
			if(digits[i] == 9){
				digits[i] = 0;
			}else{
				digits[i]++;
				return digits;
			}
		}
		//循环内未返回，则最高位为0
		int[] newDigits = new int[len + 1];
		newDigits[0] = 1;
		return newDigits;
	}
}

```
