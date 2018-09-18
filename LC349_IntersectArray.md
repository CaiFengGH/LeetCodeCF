```
package Easy;

import java.util.Arrays;
import java.util.HashSet;
import java.util.Set;

/**
 * @author Ethan
 * @desc 数组相交，不包含相同元素 
 */
public class LC349_IntersectArray {

	/**
	 * @author Ethan
	 * @desc 基于set实现
	 */
	public int[] intersectArrayWithSet(int[] num1,int[] num2){
		//1-初始化 set: intersect:
		Set<Integer> set = new HashSet<Integer>();
		Set<Integer> intersect = new HashSet<Integer>();
		
		//2-set赋值
		for(int i = 0; i < num1.length; i++){
			set.add(num1[i]);
		}
		
		//3-intersect赋值
		for(int j = 0; j < num2.length; j++){
			if(set.contains(num2[j])){
				intersect.add(num2[j]);
			}
		}
		
		int[] res = new int[intersect.size()];
		int index = 0;
		for(int k : intersect){
			res[index++] = k;
		}
		//4-返回结果
		return res;
	}
	
	/**
	 * @author Ethan
	 * @desc 基于排序思路
	 */
	public int[] intersectArrayBySort(int[] num1,int[] num2){
		//1-初始化
		Set<Integer> set = new HashSet<Integer>();
		//2-排序
		Arrays.sort(num1);
		Arrays.sort(num2);
		
		//3-基于两个指针移动
		int i = 0;
		int j = 0;
		while(i < num1.length && j < num2.length){
			if(num1[i] < num2[j]){
				i++;
			}else if(num1[i] > num2[j]){
				j++;
			}else{
				set.add(num1[i]);
				i++;
				j++;
			}
		}
		
		//4-返回结果
		int[] res = new int[set.size()];
		int index = 0;
		for(int k : set){
			res[index++] = k;
		}
		return res;
	}
	
	public static void main(String[] args) {
		LC349_IntersectArray ia = new LC349_IntersectArray();
		int[] num1 = {1,2,2,1};
		int[] num2 = {2,2};
		
		int[] res = ia.intersectArrayBySort(num1, num2);
		for(int i : res){
			System.out.println(i);
		}
	}
}

```
