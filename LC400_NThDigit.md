```
package Easy;

/**
 * @author Ethan
 * @desc 返回正整数序列中的第n的数字字符 
 */
public class LC400_NThDigit {

	/**
	 * @author Ethan
	 * @desc 
	 */
	public int nthDigit(int num){
		//1-初始化
		int numLen = 1;
		long numCount = 9;
		int start = 1;
		//2-循环，判断区间
		while(num > numLen * numCount){
			num -= numLen * numCount;
			numLen++;
			numCount *= 10;
			start *= 10;
		}
		//3-确定具体数字
		start += (num - 1) / numLen;
		String s = Integer.toString(start);
		return Character.getNumericValue(s.charAt((num - 1) % numLen));
	}
	
	public static void main(String[] args) {
		LC400_NThDigit nth = new LC400_NThDigit();
		int res = nth.nthDigit(11);
		System.out.println(res);
	}
}

```
