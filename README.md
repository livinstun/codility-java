# codility-java

## 1. BinaryGap
Find longest sequence of zeros in binary representation of an integer.

```
class Solution {
    public int solution(int N) {
        int count = 0,max = 0,flag=0;
        while(N>0){
            int r = N%2;
            N/=2;
            if(r==0 && flag==1)
                count++;
            else if(r==1){
                if(count>max)
                    max = count;
                count = 0;
                flag = 1;
            }
        }
        return max;
    }
}
```

## 2.1 OddOccurrencesInArray
Find value that occurs in odd number of elements.

```
class Solution {
    public int solution(int[] A) {
        int xor = 0;
        for(int i=0;i<A.length;i++){
            xor^=A[i];
        }
        return xor;
    }
}
```
##4.3 MissingInteger
Find the smallest positive integer that does not occur in a given sequence.

```
import java.util.HashSet;
class Solution {
    public int solution(int[] A) {
        HashSet list = new HashSet<Integer>();
        for(int i=0;i<A.length;i++){
            if(A[i]<=0)
                continue;
            list.add(A[i]);
        }
        
        if(list.isEmpty())
            return 1;

        for(int i=1;i<=A.length;i++){
            if(!list.contains(i))
                return i;
        }
        return A.length+1;
    }
}
```

## 4.4 MaxCounters
Calculate the values of counters after applying all alternating operations: increase counter by 1; set value of all counters to current maximum.

```
public int[] solution(int N, int[] A) {
        int result[] = new int[N];
        Boolean isRepeatOccured = false;
        int max = 0,repeatmax=0;
        for(int i=0;i<A.length;i++){
            if(A[i]==N+1){
                isRepeatOccured = true;
                repeatmax = max;
                continue;
            }
            
            if(isRepeatOccured && repeatmax>result[A[i]-1]){
                result[A[i]-1]= repeatmax+1;
            }else{
                result[A[i]-1]++;
            }
            
            if(max<=result[A[i]-1]){
                max = result[A[i]-1];
            }
        }
        if(isRepeatOccured){
            for(int i=0;i<N;i++){
                if(result[i]<repeatmax){
                    result[i]= repeatmax;
                }
            }
        }
        return result;
    }
```
