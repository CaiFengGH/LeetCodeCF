```
package Easy;

/**
 * @author Ethan
 * @desc 丑数，其质数只能是2 3 5
 */
public class LC263_UglyNumber {

	/**
	 * @author Ethan
	 * @desc 判断是否是丑数
	 */
	public boolean isUglyNumber(int num){
		while(num % 2 == 0) num = num >> 1;
		while(num % 3 == 0) num = num / 3;
		while(num % 5 == 0) num = num / 5;
		//无需提前进行num==1与num==0判断
		return num == 1;
	}
}
```
