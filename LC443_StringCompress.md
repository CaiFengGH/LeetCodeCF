```
package Easy;

/**
 * @author Ethan
 * @desc 字符串in-place就地压缩，即不使用中间变量 
 */
public class LC443_StringCompress {

	/**
	 * @author Ethan
	 * @desc 返回字符串就地压缩后的长度
	 */
	public int stringCompress(char[] chas){
		//1-异常参数检测
		if(chas == null || chas.length == 0){
			return -1;
		}
		
		//2-初始化 index: i: j: len: freq: ch:
		int index = 0,i = 0,j = 0,freq = 0;
		int len = chas.length;
		char ch = 0;
		
		//3-遍历
		while(i < len){
			//4-获取ch及freq
			ch = chas[i];
			j = i;
			while(j < len && chas[j] == ch){
				j++;
			}
			freq = j - i;
			//分情况讨论freq
			chas[index++] = ch;
			if(freq == 1){
			}else if(freq < 10){
				chas[index++] = (char)(freq + '0');
			}else{
				String freqStr = String.valueOf(freq);
				for(int k = 0; k < freqStr.length();k++){
					chas[index++] = freqStr.charAt(k);
				}
			}
			i = j;
		}
		//5-返回
		return index;
	}
	
	public static void main(String[] args) {
		LC443_StringCompress sc = new LC443_StringCompress();
		char[] chas = {'a'};
		int len = sc.stringCompress(chas);
		System.out.println(len);
	}
}

```
