# Candy

## 문제 분석

- 모든 아이들에게 최소 1개의 사탕을 줘야 함
- ratings가 높은 아이는 이웃한 아이보다 더 많은 사탕을 줘야 함
- 필요한 최소 사탕의 수를 리턴
- n == ratings.length
- 1 <= n <= 2 * 10^4
- 0 <= ratings[i] <= 2 * 10^4

## 풀이 (틀림)

- i : 현재 사탕을 줄 아이 인덱스
- pivot : 지금까지 사탕 개수를 확인한 아이 중 i에 가장 가까운 아이
- start : pivot 값이 변할 때 같이 값을 갱신해줘야 하는 시작 인덱스

### 로직
- ratings[pivot] < ratings[i] : arr[i]=arr[pivot]+1, pivot & start 1씩 증가
- ratings[pivot] > ratings[i] : arr[i]=1, start ~ pivot까지 1씩 증가시켜 줌
- ratings[pivot] == ratings[i] : arr[i]=1, pivot & start 1씩 증가

### 예외

- ratings: [1,3,2,2,1] 인 경우에 i=2일 때, arr[1] 이 이미 증가했었기 때문에 더해주지 않아도 1보다 더 크기 때문에 pivot의 값을 증가시켜 주지 않아도 됨
- 추후 고려 : 오름차순/내림차순 여부에 따라서 start와 pivot 위치를 결정할지

```java


                if(arr[pivot]<=arr[i]){
                    for(int j=start;j<=pivot;j++){
                        arr[j]++;
                    }
                    pivot++;
                }
                else {
                    pivot++;
                    start++;
                }


```

## 전체 코드 

```java

class Solution {
    public int candy(int[] ratings) {
        
        int[] arr=new int[ratings.length];
        int pivot=0;
        int start=0;
        arr[0]=1;

        for(int i=1;i<arr.length;i++){
            if(ratings[pivot]<ratings[i]){
                arr[i]=arr[pivot]+1;
                pivot++;
                start++;
            }
            else if(ratings[pivot]>ratings[i]){
                arr[i]=1;

                if(arr[pivot]<=arr[i]){
                    for(int j=start;j<=pivot;j++){
                        arr[j]++;
                    }
                    pivot++;
                }
                else {
                    pivot++;
                    start++;
                }
                
            }
            else {
                arr[i]=1;
                pivot++;
                start++;
            }
        }

        int sum=0;

        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
        }

        return sum;
    }
}

```
