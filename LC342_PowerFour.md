```
package Easy;

/**
 * @author Ethan
 * @desc 判断是否是4的次幂 
 */
public class LC342_PowerFour {
	
	/**
	 * @author Ethan
	 * @desc 4的次幂奇数位为1，奇数1除去
	 */
	public boolean isPowerFour(int num){
		
		return num > 0 && (num & (num - 1)) == 0 && (num & 0x55555555) != 0;
	}
}
```
