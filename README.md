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

##2. OddOccurrencesInArray
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
