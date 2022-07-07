## 선택 정렬(Selection Sort)
베열의 수가 커질 수록 시간복잡도는 커지기 때문에 비효율적인 알고리즘 중 하나.

### [문제] 해당 숫자를 정렬
 ```
 1 10 3 7 6 8 2 9 4 5
```
### [방법]
- 앞에서 하나씩 이동하며 실행
- 가장 작은 숫자를 앞으로 보내는데, 해당 번째와 와야하는 숫자의 자리를 바꾼다. 

```
번째 배열
[1] '1' 10 3 7 6 8 2 9 4 5
[2] 1 '2' 3 7 6 8 '10' 9 4 5
[3] 1 2 '3' 7 6 8 10 9 4 5
[4] 1 2 3 '4' 6 8 10 9 '7' 5
[5] 1 2 3 4 '5' 8 10 9 7 '6'
[6] 1 2 3 4 5 '6' 10 9 7 '8'
[7] 1 2 3 4 5 6 '7' 9 '10' 8
[8] 1 2 3 4 5 6 7 '8' 10 '9'
[9] 1 2 3 4 5 6 7 8 '9' '10'
```

### [시간 복잡도] O(N<sup>2</sup>)
숫자를 하나 하나 비교연산을 하기 때문에 아래와 같이 수식을 적을 수 있는데, '등차수열'이라고 한다.  
`10 + 9 + 8 + ...+ 3 + 2 + 1`  
=>  10 * (10 + 1) / 2 = 55  
=> N * (N + 1) / 2  (+와 /는 N이 커질 수록 의미X)  
=> N * N   
=> O(N<sup>2</sup>)


### [코드]
```javascript
function selection_sort() {
    let min, index, temp;
    let array = [1,10,3,7,6,8,2,9,4,5]

    for(let i=0; i<array.length; i++){
        min = 999;
        // 최솟값을 찾는다.
        for(let j=i; j<array.length; j++){
            if(min > array[j]){ 
                min = array[j]
                index = j 
            } 
        }
        // 자리를 바꿔준다.(swap)
        temp = array[i];
        array[i] = array[index];
        array[index] = temp;
        // 구조분해 할당을 이용할 수 있다.
        //[array[i], array[index]] = [array[index], array[i]]              
    }

}
```