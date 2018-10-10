```
package Easy;

/**
 * @author Ethan
 * @desc 计算两个以字符串表示的整数之和 
 */
public class LC415_AddStrings {

	public String addStrings(String num1,String num2){
		//1-初始化
		StringBuffer sb = new StringBuffer();
		int carry = 0;
		int sum1 = 0;
		int sum2 = 0;
		//2-遍历求和
		for(int i = num1.length() - 1, j = num2.length() - 1; 
				i >= 0 || j >= 0 || carry > 0; i--,j--){
			sum1 = i < 0 ? 0 : num1.charAt(i) - '0';
			sum2 = j < 0 ? 0 : num2.charAt(j) - '0';
			sb.append((sum1 + sum2) % 10);
			carry = (sum1 + sum2) / 10;
		}
		//3-返回
		
		return sb.reverse().toString();
	}
	
	public static void main(String[] args) {
		LC415_AddStrings add = new LC415_AddStrings();
		String num1 = "123";
		String num2 = "45";
		String res = add.addStrings(num1, num2);
		System.out.println(res);
	}
	
}

```
