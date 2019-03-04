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
## 2.2 CyclicRotation
Rotate an array to the right by a given number of steps.

class Solution {
    public int[] solution(int[] A, int K) {
        
        int N = A.length;
        if(N==0)
            return A;
        int rotate = K%N;
        
        int result[] = new int[A.length];
        if(rotate!=0){
            for(int i=0;i<A.length;i++){
                result[(i+rotate)%N] = A[i];
            }
            return result;
        }
        return A;
    }
}

## 3.1 FrogJmp
Count minimal number of jumps from position X to Y.

```
import java.lang.Math;
class Solution {
    public int solution(int X, int Y, int D) {
        if(X==Y)
            return 0;
        double N = (Y-X+D)/(double)D;
        return (int)Math.ceil(N)-1;
    }
}
```

## 3.2 PermMissingElem
Find the missing element in a given permutation.
```
class Solution {
    public int solution(int[] A) {
        long sum = 0;
        long n = A.length+1;
        long sumN = (n*(n+1))/2;
        
        for(int i=0;i<A.length;i++){
            sum+= A[i];
        }
        return (int)(sumN-sum);
    }
}
```

## 4.3 MissingInteger
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
class Solution {
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
 }
```
