```
package Medium;

/**
 * @author Ethan
 * @desc 
 * return minimum path sum in grid filled with non-negative number
 */
public class LC64_MinimumPathSum {

	/**
	 * @author Ethan
	 * @desc 
	 * based on dp
	 * gridSum[i][j] = Math.min(gridSum[i-1][j],gridSum[i][j-1]) + grid[i][j]
	 * gridSum[i][j]: path sum to [i,j]
	 */
	public int minimumPathSum(int[][] grid){
		//1-initate rows, cols and gridSum
		int rows = grid.length;
		int cols = grid[0].length;
		int[][] gridSum = new int[rows][cols];
		
		//2-based on dp
		for(int i = 0; i < rows;i++){
			for(int j = 0; j < cols; j++){
				if(i == 0 && j == 0){
					gridSum[i][j] = grid[i][j];
				}else if(i == 0 && j != 0){
					gridSum[i][j] = gridSum[i][j - 1] + grid[i][j];
				}else if(i != 0 && j == 0){
					gridSum[i][j] = gridSum[i - 1][j] + grid[i][j];
				}else{
					gridSum[i][j] = Math.min(gridSum[i - 1][j], gridSum[i][j - 1]) + grid[i][j];
				}
			}
		}
		
		//3-return 
		return gridSum[rows - 1][cols - 1];
	}
	
	public static void main(String[] args) {
		LC64_MinimumPathSum mps = new LC64_MinimumPathSum();
		int[][] grid = {{1,3,1},{1,5,1},{4,2,1}};
		int minPathSum = mps.minimumPathSum(grid);
		System.out.println(minPathSum);
	}
}


```
