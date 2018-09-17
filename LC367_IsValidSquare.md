```
package Easy;

/**
 * @author Ethan
 * @desc 验证给定的数是否是完全平方数 
 */
public class LC367_ValidPerfectSquare {

	/**
	 * @author Ethan
	 * @desc 奇数序列之和，1+3+5+7+9...
	 */
	public boolean isValidIWithOdd(int num){
		int i = 1;
		while(num > 0){
			num -= i;
			i += 2;
		}
		return num == 0;
	}
	
	/**
	 * @author Ethan
	 * @desc 基于二分搜索的方式
	 */
	public boolean isValidWithBinarySearch(int num){
		int left = 1;
		int right = num;
		int mid = 0;
		int res = 0;
		
		while(left <= right){
			mid = (left + right) >> 1;
			res = mid * mid;
			if(res == num){
				return true;
			}else if(res < num){
				left = mid + 1;
			}else{
				right = mid - 1;
			}
		}
		return false;
	}
	
	/**
	 * @author Ethan
	 * @desc 基于牛顿法
	 */
	public boolean isValidWithNewton(int num){
		int x = num;
		while(x * x > num){
			x = (x + num / x) >> 1;
		}
		return x * x == num;
	}
	
	public static void main(String[] args) {
		LC367_ValidPerfectSquare valid = new LC367_ValidPerfectSquare();
		int num = 15;
		
		boolean res = valid.isValidIWithOdd(num);
		System.out.println(res);
		
		res = valid.isValidWithBinarySearch(num);
		System.out.println(res);
		
		res = valid.isValidWithNewton(num);
		System.out.println(res);
	}
}

```
