```
package Medium;

/**
 * @author Ethan
 * @desc 
 * return number of unique path from top-left to bottom-right 
 * in 2D-array with obstacles
 */
public class LC63_UniquePath2 {

	/**
	 * @author Ethan
	 * @desc 
	 * based on improved dp
	 */
	public int uniquePath(int[][] obstacleGrid){
		//1-initate width
		int width = obstacleGrid[0].length;
		
		//2-initate dp 
		int[] dp = new int[width];
		dp[0] = 1;
		
		//3-iterate grids
		for(int[] row : obstacleGrid){
			for(int i = 0; i < width; i++){
				if(row[i] == 1){
					dp[i] = 0;
				}else if(i > 0){
					dp[i] += dp[i - 1];
				}
			}
		}
		
		//4-return number
		return dp[width - 1];
	}
	
	public static void main(String[] args) {
		LC63_UniquePath2 up = new LC63_UniquePath2();
		int[][] obstacleGrid = {{0,0,0},{0,1,0},{0,0,0}}; 
		int num = up.uniquePath(obstacleGrid);
		System.out.println(num);
	}
}

```
