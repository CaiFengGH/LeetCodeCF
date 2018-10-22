```
package Medium;

/**
 * @author Ethan
 * @desc 
 * search target is in 2D array
 * each row sorted from left to right
 * first number of next row is greater than last number of previous row
 */
public class LC74_SearchIn2DArray {

	/**
	 * @author Ethan
	 * @desc 
	 * search from top-right 
	 */
	public boolean isIn2DArray(int[][] array,int target){
		//1-initate
		int length = array.length;
		int width = array[0].length;
		int i = 0, j = width - 1;
		
		//2-search
		while(i < length && j >= 0){
			if(array[i][j] == target){
				return true;
			}else if(array[i][j] > target){
				j--;
			}else{
				i++;
			}
		}
		return false;
	}
	
	public static void main(String[] args) {
		LC74_SearchIn2DArray search = new LC74_SearchIn2DArray();
		int[][] array = {{1,3,5,7},{10,11,16,20},{23,30,34,50}};
		int target = 17;
		boolean isIn = search.isIn2DArray(array, target);
		System.out.println(isIn);
	}
}

```
