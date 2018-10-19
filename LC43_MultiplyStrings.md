```
package Medium;

/**
 * @author Ethan
 * @desc 
 * two number represented as string multiply, and result represented as string
 */
public class LC43_MultiplyStrings {

	/**
	 * @author Ethan
	 * @desc 
	 */
	public String multiplyStrings(String num1,String num2){
		//1-initial length of num 
		int len1 = num1.length();
		int len2 = num2.length();
		
		//2-initial int[] array
		int[] res = new int[len1 + len2];
		
		//3-iterate 
		for(int i = len1 - 1; i >= 0; i--){
			for(int j = len2 - 1; j >= 0; j--){
				int mul = (num1.charAt(i) - '0') * (num2.charAt(j) - '0');
	
				//4-num1[i] * num2[j] = res[i+j,i+j+1]
				int index1 = i + j;
				int index2 = i + j + 1;
				int sum = mul + res[index2];
				
				res[index1] += sum / 10;
				res[index2] = sum % 10;
			}
		}
		
		//5-initial StringBuilder
		StringBuffer sb = new StringBuffer();
		int index = 0;
		while(res[index] == 0){ index++;}
		
		for(int k = index; k < len1 + len2; k++){
			sb.append(res[k]);
		}
		//6-return
		return sb.length() == 0 ? "0" : sb.toString();
	}
	
	public static void main(String[] args) {
		LC43_MultiplyStrings ms = new LC43_MultiplyStrings();
		String num1 = "123";
		String num2 = "456";
		String res = ms.multiplyStrings(num1, num2);
		System.out.println("num1 x num2 = ?");
		System.out.println(num1 +" x "+ num2 +" = " + res);
	}
}
```
