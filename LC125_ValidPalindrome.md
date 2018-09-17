```
package CaiFeng;

public class LC125_ValidPalindrome {
	/**
	 * @author Ethan
	 * @desc 判断一个字符串是否是回文串
	 */
	public boolean validPalindrome(String s){
		//参数异常
		if(s.isEmpty()){
			return true;
		}
		//初始化左右前后两个指针
		int head = 0;
		int tail = s.length() - 1;
		char headCha;
		char tailCha;
		//循环判定
		while(head <= tail){
			headCha = s.charAt(head);
			tailCha = s.charAt(tail);
			if(!Character.isLetterOrDigit(headCha)){
				head++;
			}else if(!Character.isLetterOrDigit(tailCha)){
				tail--;
			}else{
				if(Character.toLowerCase(headCha) != Character.toLowerCase(tailCha)){
					return false;
				}else{
					head++;
					tail--;
				}
			}
		}
		return true;
	}
}

```
