```
package Easy;

import java.util.HashSet;
import java.util.PriorityQueue;
import java.util.Set;

/**
 * @author Ethan
 * @desc 返回整数数组中第三大的元素 
 */
public class LC414_ThirdMaxNum {

	/**
	 * @author Ethan
	 * @desc 基于变量移动方法
	 */
	public int thirdMaxByMax(int[] nums){
		//1-异常参数检测
		if(nums == null || nums.length == 0){
			System.out.println("数组不合法");
			return -1;
		}
		
		//2-初始化变量 用引用类型
		Integer max1th = null;
		Integer max2th = null;
		Integer max3th = null;
		
		//3-遍历数组
		for(Integer i : nums){
			if(i.equals(max1th) || i.equals(max2th) || i.equals(max3th)){
				continue;
			}
			if(max1th == null || i > max1th){
				max3th = max2th;
				max2th = max1th;
				max1th = i;
			}else if(max2th == null || i > max2th){
				max3th = max2th;
				max2th = i;
			}else{
				max3th = i;
			}
		}
		//4-返回结果
		return max3th == null ? max1th : max3th;
	}
	
	/**
	 * @author Ethan
	 * @desc 基于优先队列方式实现 
	 */
	public int thirdMaxByPQ(int[] nums){
		//1-异常参数检测
		if(nums == null || nums.length == 0){
			System.out.println("数组不合法");
			return -1;
		}
		//2-初始化 pq: set: 优先级队列按照自然顺序升序排序
		PriorityQueue<Integer> pq = new PriorityQueue<Integer>();  
		Set<Integer> set = new HashSet<Integer>();
		int tmp = 0;
		
		//3-遍历数组
		for(int i = 0; i < nums.length; i++){
			tmp = nums[i];
			if(!set.contains(tmp)){
				pq.offer(tmp);
				set.add(tmp);
				//pq长度保持为3个
				if(pq.size() > 3){
					set.remove(pq.poll());
				}
			}
		}
		
		//4-无第三大则返回最大值
		if(pq.size() < 3){
			while(pq.size() > 1){
				pq.poll();
			}
		}
		//5-返回
		return pq.peek();
	}
	
	public static void main(String[] args) {
		LC414_ThirdMaxNum third = new LC414_ThirdMaxNum();
		int[] nums = {1,2,2,3};
		int thirdMax = third.thirdMaxByMax(nums);
		System.out.println(thirdMax);
	}
}

```
