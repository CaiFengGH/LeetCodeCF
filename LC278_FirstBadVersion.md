```
package Easy;

/**
 * @author Ethan
 * @desc 查找第一个坏版本 
 */
public class LC278_FirstBadVersion {

	/**
	 * @author Ethan
	 * @desc 基于二分搜索
	 */
	public int firstBadVersion(int[] nums){
		//1-初始化
		int start = 0;
		int end = nums.length - 1;
		int mid = 0;
		//2-确定第一个坏版本
		while(start < end){
			//关键点，避免溢出
			mid = start + (end - start)/2;
			if(isBadVersion(mid)){
				end = mid - 1;
			}else{
				start = mid + 1;
			}
		}
		return start;
	}
	
	/**
	 * @author Ethan
	 * @desc 由系统提供
	 */
	public boolean isBadVersion(int version){
		return false;
	}
}

```
