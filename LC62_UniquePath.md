```
package Medium;

/**
 * @author Ethan
 * @desc 
 * return number of unique path from top-left to bottom-right in 2D-array 
 */
public class LC62_UniquePath {

	/**
	 * @author Ethan
	 * @desc 
	 * based on dp
	 * map[i][j] = map[i-1][j] + map[i][j-1]
	 */
	public int uniquePath(int rows,int cols){
		//1-initate map
		int[][] map = new int[rows][cols];
		
		//2-initate map[][0]
		for(int i = 0; i < rows; i++){
			map[i][0] = 1;
		}
		
		//3-initate map[0][]
		for(int j = 0; j < cols; j++){
			map[0][j] = 1;
		}
		
		//4-initate map[i][j]
		for(int k = 1; k < rows;k++){
			for(int m = 1; m < cols; m++){
				map[k][m] = map[k - 1][m] + map[k][m - 1];
			}
		}
		
		//5-return result
		return map[rows - 1][cols - 1];
	}

	public static void main(String[] args) {
		LC62_UniquePath up = new LC62_UniquePath();
		int num = up.uniquePath(7, 3);
		System.out.println(num);
	}
}

```
