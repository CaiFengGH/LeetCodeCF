```
package Easy;

/**
 * @author Ethan
 * @desc 数字根问题
 * 数字根性质：https://www.cnblogs.com/vincent93/p/6686423.html
 */
public class LC258_AddDigitals {

	/**
	 * @author Ethan
	 * @desc 
	 */
	public int addDigitals(int num){
		return 1 + (num - 1) % 9;
	}
}

```
