# reduce()란??
배열의 각 요소에 대해 주어진 함수를 실행하고 결과값을 반환한다.
누산기(acc), 현재 값(cur), 현재 인덱스(idx), 원본배열(src) 네가지 인자를 가진다.

>arr.reduce(callback [ , initialValue])

callback 에는 위의 네가지 인자가 들어가게되며 initialValue 값에는 초기값을 설정해준다.
최초 호출 때 initialValue 가 있는 경우 acc는 initial과 같고 cur은 배열의 첫번째 값과 같다.
최초 호출 때 initialValue 가 없는 경우 acc는 배열의 첫번째 값과 같고 cur은 두번째와 같다.

```javascript

[0,1,2,3,4].reduce(function(acc,curr,idx,src){
    return acc + cur;
});

[0,1,2,3,4].reduce((prev,curr)=>prev+curr,0); // 초기값으로 0을 줌.
```  

#
#

||acc|cur|idx|src|반환 값|
|--|--|--|--|--|--|
|1번째호출|0|1|1|[0,1,2,3,4]|1|
|2번째호출|1|2|2|[0,1,2,3,4]|3|
|3번째호출|3|3|3|[0,1,2,3,4]|6|
|4번째호출|6|4|4|[0,1,2,3,4]|10|




#
#
#
## 객체 배열에서의 값 합산
```javascript
var initialValue = 0;
var sum = [{x: 1}, {x:2}, {x:3}].reduce(
    (accumulator, currentValue) => accumulator + currentValue.x
    ,initialValue
);

console.log(sum) // logs 6
```
---
#
#

## 중첩 배열 펼치기
```javascript
var flattened = [[0, 1], [2, 3], [4, 5]].reduce(
  ( accumulator, currentValue ) => accumulator.concat(currentValue),
  []
);
```
---
#
#
## 객체 내의 값 인스턴스 개수 세기
```javascript
var names = ['Alice', 'Bob', 'Tiff', 'Bruce', 'Alice'];

var countedNames = names.reduce(function (allNames, name) {
  if (name in allNames) {
    allNames[name]++;
  }
  else {
    allNames[name] = 1;
  }
  return allNames;
}, {});
// countedNames is:
// { 'Alice': 2, 'Bob': 1, 'Tiff': 1, 'Bruce': 1 }
```

*[mdn사이트의 reduce() 함수 link](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)*

