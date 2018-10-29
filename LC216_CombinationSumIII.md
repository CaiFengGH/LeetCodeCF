```
package Medium;

import java.util.ArrayList;
import java.util.List;

/**
 * @author Ethan
 * @desc 
 * k number only contain 1 to 9 and sum is n
 * input:k=3,n=7
 * output:1,2,4
 */
public class LC216_CombinationSumIII {
	
	public List<List<Integer>> combinationSum(int k,int n){
		//1-detect exception
		if(k < 1 || n < 1) return null;
		
		//2-initate
		List<List<Integer>> res = new ArrayList<>();
		
		//3-backtrack
		backtrack(res,new ArrayList<Integer>(),k,1,n);
		//4-return
		return res;
	}

	private void backtrack(List<List<Integer>> res,
			ArrayList<Integer> tmpList, int k, int start, int n) {
		if(tmpList.size() == k && n == 0){
			res.add(new ArrayList<Integer>(tmpList));
			return;
		}
		for(int i = start; i <= 9; i++){
			tmpList.add(i);
			backtrack(res,tmpList,k,i+1,n-i);
			tmpList.remove(tmpList.size() - 1);
		}
	}
	
	public void printList(List<List<Integer>> ll){
		if(ll == null) return;
		for(List<Integer> l : ll){
			for(Integer i : l){
				System.out.print(i+" ");
			}
			System.out.println();
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC216_CombinationSumIII cs = new LC216_CombinationSumIII();
		int k = 3;
		int n = 7;
		List<List<Integer>> res = cs.combinationSum(k, n);
		cs.printList(res);
	}
}
```
