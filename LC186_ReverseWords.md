```
package CaiFeng;

/**
 * @author Ethan
 * @desc 实现字符串中单词反转 
 */
public class LC186_ReverseWords {

	public void reverseWords(char[] cha){
		//1-第一次反转
		int pos = 0;
		//<=保证最后一个单词也反转
		for(int i = 0; i <= cha.length; i++){
			//遇到' '即单词结束
			if(i < cha.length && cha[i] != ' '){
				continue;
			}
			reverse(cha,pos,i-1);
			pos = i + 1;
		}
		
		//2-第二次反转
		reverse(cha,0,cha.length-1);
	}

	/**
	 * @author Ethan
	 * @desc 基于双指针反转单词 
	 */
	public void reverse(char[] cha, int from, int to) {
		//1-初始化临时字符 c
		char c = 0;
		//2-循环反转
		while(from < to){
			c = cha[from];
			cha[from] = cha[to];
			cha[to] = c;
			from++;
			to--;
		}
	}
}

```
