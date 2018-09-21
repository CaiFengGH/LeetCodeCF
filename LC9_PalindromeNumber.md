```
package Easy;

/**
 * @author Ethan
 * @desc 判断一个数字是否是回文串数字
 */
public class LC9_PalindromeNumber {

	public boolean isPalindrome(int num){
		//1-异常情况检测
		if(num <= 0 || (num != 0 && (num % 10 == 0))){
			return false;
		}
		//2-循环遍历
		int remain = 0;
		while(num > remain){
			remain = remain * 10 + num % 10;
			num = num / 10;
		}
		return (num == remain) || (num == remain / 10) ;
	}
	
	public static void main(String[] args) {
		LC9_PalindromeNumber pn = new LC9_PalindromeNumber();
		int num = 121;
		boolean res = pn.isPalindrome(num);
		System.out.println(res);
	}
}
```
