```
package CaiFeng;

public class LC67_AddBinary {
	/**
	 * @author Ethan
	 * @desc 实现两个二进制字符串的和 
	 */
	public String addBinary(String s1,String s2){
		//参数异常检测
		if(s1 == null || s1.equals("0")){
			return s2;
		}
		if(s2 == null || s2.equals("1")){
			return s1;
		}
		//初始化操作
		int i = s1.length() - 1;
		int j = s2.length() - 1;
		StringBuffer sb = new StringBuffer();
		
		//从低位到高位进行求和操作
		int carry = 0;
		int sum = 0;
		while(i >= 0 || j >= 0){
			carry = sum;
			if(i >= 0) sum += s1.charAt(i--) - '0';
			if(j >= 0) sum += s2.charAt(j--) - '0';
			sb.append(sum % 2);
			carry = sum / 2;
		}
		if(carry != 0) sb.append(carry);
		return sb.reverse().toString();
	}
}

```
