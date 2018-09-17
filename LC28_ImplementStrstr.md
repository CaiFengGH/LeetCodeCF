```
package CaiFeng;

public class LC28_ImplementStrstr {
	
	/**
	 * @author Ethan
	 * @desc 寻找子串首次出现索引
	 */
	public int implementStrstr(String haystack,String needle){
		//异常参数检查
		int haystackLen = haystack.length();
		int needleLen = needle.length();
		if(haystackLen < needleLen){
			return -1;
		}
		if(needleLen == 0){
			return 0;
		}
		int rest = haystackLen - needleLen;
		//遍历搜索
		for(int i = 0; i <= rest; i++){
			if(haystack.substring(i,i+needleLen).equals(needle)){
				return i;
			}
		}
		return -1;
	}
}

```
