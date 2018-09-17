```
package CaiFeng;

/**
 * @author Ethan
 * @desc 将字符串转换为整型 
 */
public class LC8_MyAtoi {

	/**
	 * @author Ethan
	 * @desc 去除前面的空格+注意前面的正负号+是否超过整型最大值+是否小于整型最小值
	 */
	public int myAtoi(String str){
		//1-异常参数检测
		if(str == null || str.length() == 0){
			return 0;
		}
		//2-去除空格
		str = str.trim();
		//3-判断正负号，可能存在也可能不存在
		boolean positive = true;
		int index = 0;
		if(str.charAt(index) == '+'){
			positive = true;
			index++;
		}else if(str.charAt(index) == '-'){
			positive = false;
			index++;
		}
		
		//4-获取数字，初始化为double的64位
		double temp = 0;
		int digital = 0;
		for(; index < str.length(); index++){
			digital = str.charAt(index) - '0';
			//非数字直接跳出循环
			if(digital < 0 || digital > 9){
				break;
			}
			//根据positive生成数字
			if(positive){
				temp = temp * 10 + digital;
				if(temp > Integer.MAX_VALUE){
					return Integer.MAX_VALUE;
				}
			}else{
				temp = temp * 10 - digital;
				if(temp < Integer.MIN_VALUE){
					return Integer.MIN_VALUE;
				}
			}
		}
		//5-强转为int类型
		return (int) temp;
	}
}
```
