```
package Easy;

/**
 * @author Ethan
 * @desc 计算一个字符串中的segment的数量
 */
public class LC434_CountSegments {

	/**
	 * @author Ethan
	 * @desc 
	 */
	public int countSegments(String s){
		//1-异常参数检测
		if(s == null || s.length() == 0){
			return 0;
		}
		//2-初始化
		s = s.trim();
		int res = 0;
		//3-遍历统计
		for(int i = 0; i < s.length();i++){
			if(s.charAt(i) != ' ' &&(i == 0 || s.charAt(i-1) == ' ')){
				res++;
			}
		}
		return res;
	}
	
	public static void main(String[] args) {
		LC434_CountSegments cs = new LC434_CountSegments();
		String s = "Hello, my name is John ";
		int res = cs.countSegments(s);
		System.out.println("Number of Segments : " + res);
	}
}
```
