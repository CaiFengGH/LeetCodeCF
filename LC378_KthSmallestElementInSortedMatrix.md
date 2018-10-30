```
package Medium;

import java.util.PriorityQueue;

/**
 * @author Ethan
 * @desc 
 * kth smallest element in a sorted matrix
 * input:
 * 1 5 9
 * 2 6 10
 * 3 7 11
 * k = 8
 * output:
 * 10
 */
public class LC378_KthSmallestElementInSortedMatrix {

	/**
	 * @author Ethan
	 * @desc 
	 * based on PriorityQueue
	 */
	public int kthSmallestElement(int[][] nums,int k){
		//1-detect exception
		if(nums == null || nums.length < 1) return -1;
		
		//2-initate
		PriorityQueue<Tuple> pq = new PriorityQueue<Tuple>(); 
		int cols = nums[0].length;
		
		for(int i = 0; i < cols; i++){
			pq.offer(new Tuple(0, i, nums[0][i]));
		}
		
		//3-iterate
		for(int j = 0; j < k - 1; j++){
			Tuple t = pq.poll();
			if(t.row == nums.length - 1) continue;
			pq.offer(new Tuple(t.row + 1, t.col, nums[t.row + 1][t.col]));
		}
		
		//4-return
		return pq.poll().val;
	}
	
	public static void main(String[] args) {
		LC378_KthSmallestElementInSortedMatrix kth = 
				new LC378_KthSmallestElementInSortedMatrix();
		
		int[][] nums = {{1,5,9},{2,6,10},{3,7,11}};
		int k = 8;
		int res = kth.kthSmallestElement(nums, k);
		System.out.println(res);
	}
}
class Tuple implements Comparable<Tuple>{
	public int row;
	public int col;
	public int val;
	
	public Tuple(int row,int col,int val){
		this.row = row;
		this.col = col;
		this.val = val;
	}

	@Override
	public int compareTo(Tuple t) {
		return this.val - t.val;
	}
}
```
