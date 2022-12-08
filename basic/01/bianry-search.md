# Binary-search
이진 탐색(검색)은 데이터가 정렬돼 있는 배열에서 특정한 값을 찾아내는 알고리즘이다.

### 이진 탐색 예시
아래와 같이 오름차순으로 정렬되어 있는 배열이 있다고 할 때, 80의 값을 찾아보자.
```
[10, 20, 30, 47, 56, 68, 80, 83, 99, 100]
```

1. 임의의 값 `47`을 선택한다.
1. 선택한 값 `47`과 찾고자 하는 값 `80`을 비교한다.
1. `47 < 80`이므로 `80`은 `47`의 우측에 존재한다는 것을 알 수 있다.
1. `47`을 기준으로 우측에 있는 배열 값들을 대상으로 이어서 탐색을 진행한다.
1. `[56, 68, 80, 83, 99, 100]` 배열에서 임의의 값 `68`을 선택한다.
1. `68 < 80`이기 때문에 마찬가지로 68 우측에 위치하는 것을 알 수 있다.
1. `68`을 기준으로 우측에 있는 배열 값들에서 다시 탐색을 진행한다.
1. `[80, 83, 99, 100]`에서 임의의 값 `80`을 선택한다.
1. `80 === 80`으로 원하는 값을 찾고 탐색을 종료한다.

### 코드 구현
```
const arr = [];
for (let i = 1; i <= 10000; i++) {
  arr.push(i);
}
 
function binarySearch (target, dataArray) {
  let low = 0;
  let high = dataArray.length - 1;
  
  let index = 0;
  while (low <= high) {
    let mid = Math.floor((high + low) / 2);
    let guess = dataArray[mid];
 
    if (guess === target) {
      return guess;
    } else if (guess > target) {
      high = mid - 1;
    } else {
      low = mid + 1;
    }
    index++;
  }
  return -1;
}
```