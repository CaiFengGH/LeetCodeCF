```
package CaiFeng;

/**
 * @author Ethan
 */
public class LC14_LongestCommonPrefix {
	
	public String longestCommonPrefix(String[] strs){
		//参数异常检测
		if(strs == null || strs.length == 0){
			return null;
		}
		
		//初始化current
		String current = strs[0];
		
		for(int index = 1; index < strs.length; index++){
			//寻找相邻元素的最长公共前缀
			while(strs[index].indexOf(current) != 0 ){
				current = current.substring(0, current.length() - 1);
			}
		}
		return current;
	}
}

```
