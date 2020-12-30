## 1

- 문제
    - 1부터 N까지 정렬된 숫자가 들어있는 배열을 스택을 이용해 순서를 바꾸려고 한다. 이 때 스택을 이용하여 오름차순으로 정렬된 배열을 주어진 배열 arr로 바꿀 수 있는지 확인하는 solution 함수를 작성하라.

```
public boolean solution(int[] arr){
        int arr_size = arr.length;
        int prev_val = arr[0];
        int max_val = 0;
        
        if(arr_size == 1) return true; // 갯수 하나면 가능
        
        // 이전값, 다음값 차이가 1이 아니면 스택으로 정렬 불가능. 1이면 가능
        for(int i = 1 ; i < arr_size ; i++){
            if(arr[i] > max_val) {
                max_val = arr[1];
            }
            if(Math.abs(arr[i] - prev_val) != 1){
                if(prev_val > arr[i]) return false;
                for(int j = i + 1; j < arr_size; j++){
                    if(Math.abs(arr[j] - prev_val) != 1){
                        if(Math.abs(arr[j] - max_val) == 1){
                            break; // 3,2,1,4,5,6,8,7 같은 경우 가능
                        }
                        return false;
                    }
                }
            }
            
            prev_val = arr[i];
        }
        
        return true;
    }
```