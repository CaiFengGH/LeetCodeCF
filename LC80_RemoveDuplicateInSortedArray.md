```
package Medium;

/**
 * @author Ethan
 * @desc 
 * duplicate value appears most twice 
 */
public class LC80_RemoveDuplicateInSortedArray {

	/**
	 * @author Ethan
	 * @desc 
	 */
	public int removeDuplicate(int[] arr){
		//1-initate index
		int i = 0;
		
		//2-itarate
		for(int n : arr){
			if(i < 2 || n > arr[i - 2]){
				arr[i++] = n;
			}
		}
		return i;
	}
	
	public static void main(String[] args) {
		LC80_RemoveDuplicateInSortedArray remove = new 
				LC80_RemoveDuplicateInSortedArray(); 
		int[] arr = {1,1,1,2,2,3};
		int newLen = remove.removeDuplicate(arr);
		System.out.println(newLen);
	}
}

```
