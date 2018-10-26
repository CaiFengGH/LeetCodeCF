```
package Medium;

import java.util.Comparator;
import java.util.LinkedList;
import java.util.List;

/**
 * @author Ethan
 * @desc 
 * merge intervals
 * input:[1,3],[2,6],[8,10],[15,18]
 * output:[[1,6],[8,10],[15,18]]
 */
public class LC56_MergeIntervals {

	/**
	 * @author Ethan
	 * @desc 
	 */
	public List<Interval> mergeIntervals(List<Interval> intervals){
		//1-detect exception
		if(intervals == null || intervals.size() <= 1) return intervals;
		
		//2-sort by interval.start
		intervals.sort(new Comparator<Interval>(){
			@Override
			public int compare(Interval i1, Interval i2) {
				return Integer.compare(i1.start, i2.start);
			}
		});
		
		//3-initate res,start and end
		List<Interval> res = new LinkedList<Interval>();
		int start = intervals.get(0).start;
		int end = intervals.get(0).end;
		
		//4-merge
		for(Interval i : intervals){
			if(i.start <= end) end = Math.max(i.end, end);
			else{
				res.add(new Interval(start,end));
				start = i.start;
				end = i.end;
			}	
		}
		//5-add the last interval
		res.add(new Interval(start,end));
		//6-return
		return res;
	}
	
	/**
	 * @author Ethan
	 * @desc print intervals
	 */
	public void printIntervals(List<Interval> intervals){
		if(intervals == null){
			return;
		}
		for(Interval i : intervals){
			System.out.println("["+i.start+","+i.end+"]");
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		LC56_MergeIntervals merge = new LC56_MergeIntervals();
		Interval i1 = new Interval(1,4);
		Interval i2 = new Interval(4,5);
		List<Interval> intervals = new LinkedList<Interval>();
		intervals.add(i1);
		intervals.add(i2);
		
		System.out.println("before merge:");
		merge.printIntervals(intervals);
		
		System.out.println("after merge:");
		List<Interval> mergedIntervals = merge.mergeIntervals(intervals);
		merge.printIntervals(mergedIntervals);
	}
}
class Interval{
	int start;
	int end;
	Interval(){}
	Interval(int start,int end){
		this.start = start;
		this.end = end;
	}
}
```
