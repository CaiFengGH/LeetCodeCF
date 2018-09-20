```
package Easy;

/**
 * @author Ethan
 * @desc 计算小于给定数字的质数的个数 
 */
public class LC204_CountPrimes {

	/**
	 * @author Ethan
	 * @desc 计算质数
	 */
	public int countPrimes(int num){
		//1-初始化
		boolean[] isPrime = new boolean[num]; 
		int count = 0;
		//2-统计数量
		for(int i = 2; i < num;i++){
			if(isPrime[i] == false){
				count++;
				for(int j = 2; i * j < num;j++){
					isPrime[i * j] = true;
				}
			}
		}
		return count;
	}
	
	public static void main(String[] args) {
		LC204_CountPrimes cp = new LC204_CountPrimes();
		int res = cp.countPrimes(10);
		System.out.println(res);
	}
}

```
