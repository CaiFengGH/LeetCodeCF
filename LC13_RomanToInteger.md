```
package CaiFeng;

public class LC13_RomanToInteger {
	
	/**
	 * @author Ethan
	 * @desc 小的数字在大的数字右边相加，否则相减
	 */
	public int romanToInteger(String s){
		//初始化数组
		int strLen = s.length();
		int[] nums = new int[strLen];
		
		//记录每个字符的大小
		for(int i=0; i < strLen; i++){
			switch (s.charAt(i)) {
				case 'M':
					nums[i] = 1000;
					break;
				case 'D':
					nums[i] = 500;
					break;
				case 'C':
					nums[i] = 100;
					break;
				case 'L':
					nums[i] = 50;
					break;
				case 'X':
					nums[i] = 10;
					break;
				case 'V':
					nums[i] = 5;
					break;
				case 'I':
					nums[i] = 1;
					break;
			}
		}
		//罗马计数规则：小数在大数右边相加，否则相减；
		int sum = 0;
		for(int j = 0; j < strLen - 1; j++){
			if(nums[j] < nums[j+1]){
				sum -= nums[j];
			}else{
				sum += nums[j];
			}
		}
		//最后一个元素直接相加
		sum += nums[strLen - 1];
		return sum;
	}
}

```
