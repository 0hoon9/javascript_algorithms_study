# Hanoi-tower
하노이 탑(Tower of Hanoi)은 퍼즐의 일종이다. 세 개의 기둥과 이 기동에 꽂을 수 있는 크기가 다양한 원판들이 있고, 퍼즐을 시작하기 전에는 한 기둥에 원판들이 작은 것이 위에 있도록 순서대로 쌓여 있다. 게임의 목적은 다음 두 가지 조건을 만족시키면서, 한 기둥에 꽂힌 원판들을 그 순서 그대로 다른 기둥으로 옮겨서 다시 쌓는 것dl다.
1. 한 번에 하나의 원판만 옮길 수 있다.
1. 큰 원판이 작은 원판 위에 있어서는 안된다.

### 문제풀이 애니메이션
![하노이탑 문제풀이](./Tower-of-hanoi.gif)
> 출처: [hackerearth](https://www.hackerearth.com/blog/developers/tower-hanoi-recursion-game-algorithm-explained/)

```
const answer = [];

function hanoi (n, from, to) {
  const by = 6-from-to;

  if (n === 1) {
    answer.push([from, to]);
  } else {
    hanoi(n - 1, from, by);
    answer.push([from, to]);
    hanoi(n - 1, by, to);
  }
}
hanoi(n, 1, 3);

// 비재귀 방식 (스택)

const result = []; 
function hanoi (n, from, to) {
  const arr = [];
  let temp = 1;
  let by = 6 - from - to;
  while (temp > 0) {
    while (n >1) {
      arr.push(to);
      arr.push(by);
      arr.push(from);
      arr.push(n);
      n--;
      arr.push(to);
      to = by;
      by = arr.pop();
    }
    result.push([from, to]);
    if (arr.length -1 > 0) {
      n = arr.pop();
      from = arr.pop();
      by = arr.pop();
      to = arr.pop();
      result.push([from, to]);
      n--;
      arr.push(from);
      from = by;
      by = arr.pop();
    } else {
      temp = 0;
    }
  }
}
hanoi (n, 1, 3);

// 최소 움직임 구하는 공식
2^n − 1,
```