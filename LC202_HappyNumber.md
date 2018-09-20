```
package Easy;

import java.util.HashSet;
import java.util.Set;

/**
 * @author Ethan
 * @desc 判断一个数字是否是happy number 
 */
public class LC202_HappyNumber {

	public boolean isHappy(int num){
		//1-初始化
		Set<Integer> set = new HashSet<Integer>();
		int squareNum = 0;
		int remain = 0;
		
		//2-遍历计算
		while(set.add(num)){
			squareNum = 0;
			while(num > 0){
				remain = num % 10;
				squareNum += remain * remain;
				num = num / 10;
			}
			System.out.println(squareNum);
			
			if(squareNum == 1){
				return true;
			}else{
				num = squareNum;
			}
		}
		return false;
	}
	
	public static void main(String[] args) {
		LC202_HappyNumber hn = new LC202_HappyNumber();
		int num = 19;
		boolean isHappy = hn.isHappy(num);
		System.out.println(isHappy);
	}
}

```
