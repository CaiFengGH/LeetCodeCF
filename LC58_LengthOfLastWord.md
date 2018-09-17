```
package CaiFeng;

/**
 * @author Ethan
 */
public class LC58_LengthOfLastWord {
	/**
	 * @author Ethan
	 */
	public int lengthOfLastWord(String s){
		//去除首位两端的空格
		s = s.trim();
		
		//定位最后一个空格的位置
		int rest = s.lastIndexOf(" ") + 1;
		
		return s.length() - rest;
	}
}

```
