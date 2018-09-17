```
package Easy;

/**
 * @author Ethan
 * @desc 基于比特操作实现整数和 
 */
public class LC371_SumOfTwoInteger {

	/**
	 * @author Ethan
	 * @desc 实现和
	 */
	public int getSum(int a,int b){
		//1-异常参数检测
		if(a == 0) return b;
		if(b == 0) return a;
		
		int carry = 0;
		//2-基于比特位操作
		while(b != 0){
			carry = a & b;
			a = a ^ b;
			b = carry << 1;
		}
		return a;
	}
	
	/**
	 * @author Ethan
	 * @desc 实现减法
	 */
	public int getSubtract(int a,int b){
		int tmp = 0;
		while(b != 0){
			tmp = ~a & b;
			a = a ^ b;
			b = tmp << 1;
		}		
		return a;
	}
	
	/**
	 * @author Ethan
	 * @desc 获取相反数
	 */
	public int getNegative(int a){
		return ~a + 1;
	}
	
	public static void main(String[] args) {
		LC371_SumOfTwoInteger arithmetic = new LC371_SumOfTwoInteger();
		int res = arithmetic.getSum(10, 22);
		System.out.println(res);
		
		res = arithmetic.getSubtract(10, 22);
		System.out.println(res);
		
		res = arithmetic.getNegative(-10);
		System.out.println(res);
	}
}

```
