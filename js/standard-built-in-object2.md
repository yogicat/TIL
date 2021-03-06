### Standard Built-in Object 2 


---

### Array

- Arrays are list-like objects whose prototype has methods to perform traversal and mutation oprations.
- An array's length can change at any time, and data can be stored at non-contiguous locations in the array



#### Array.length 

- The length property of an object which is an instance of type `Array` sets or returns the number of elements in that array.

---

#### Array.isArray()

- determines whether the passed value is an Array

---

####  Array.prototype.indexOf()

- returns the first index at which a given element can be found in the aray
- returns `-1` if it is not present
- `arr.indexOF(searchElement[, fromIndex])`
- `indexOf()` compares `searchElement` to elements of the Array using **strict equality**


---

#### Array.prototype.concat()

- used to merge two or more arrays
- return a **new Array instance**
- `var newArr = oldArr.concat(value[, value2 [,... valueN]])`
- 두개 이상의 배열을 합친다. (값으로 합친다)
- 인자(arguments)는 배열일 수도 있고 값일 수도 있다
- 새로운 배열을 반환함 (받아줘야한다)

---

**`concat` method는 arguments로 주어진 배열들과 this를 바꾸지 않고 shallow copy를 반환한다. 원본배열의 요소들이 새로운 배열로 복사되는 방법은 다음과 같다**

- Object references (not the actual object)일 경우`concat`은 참조값을 복사한다. 원본 배열과 새로운 배열은 **같은 곳**을 참조한다. 참조된 객체가 변경될 경우, 변경사항은 새로운 배열과 워본 배열에 둘 다 보인다. This inclusdes elements of array arguments that are also arrays.
- strings, numbers and booleans (not String, Number, and Boolean objects) : `concat`은 값으로써 복사를 한다. 따라서 새로운 배열과 원본배열은 서로 영향을 끼치지 않는다.

> Concatenating array(s)/value(s) will leave the originals untouched. Furthermore, any operation on the new array (except operations on elements which are object references) will have no effect on the original arrays, and vice versa.


 ```js
// Concatenating values to an array
var alpha = ['a', 'b', 'c'];

var alphaNumeric = alpha.concat(1, [2, 3]);

console.log(alphaNumeric); 
// results in ['a', 'b', 'c', 1, 2, 3]

 ```


```js
// Concatenation nested arrays
var num1 = [[1]];
var num2 = [2, [3]];

var nums = num1.concat(num2);

console.log(nums);
// results in [[1], 2, [3]]

// modify the first element of num1
num1[0].push(4);

console.log(nums);
// result in [[1, 4], 2, [3]]

```

---

#### Array.prototype.join()

- `arr.join([seperator])`
- seperator : optional / 
- **returns a string** with all array elements joined

---
### pop, push, unshift, shift 원본배열 변경

#### Array.prototype.pop()

- `push`와 반대로 배열의 마지막 요소를 뺀다(리턴)


#### Array.prototype.push()

- 배열의 마지막 인덱스에 argument값을 추가
- 배열의 새로운 길이값을 반환한다 (new length)
---

#### Array.prototype.reverse()

- 배열 요소 순서를 반대로 변경

---

#### Array.prototype.slice()

- returns a shallow copy of a portion of an array into a new array.
- `arr.slice([begin[, end]]);`
- slice new array from `begin` to `end` 

---

#### Array.prototype.splice()

- **change the contents of an array** by removing existing elements or adding new elements.
- `array.splice(startIndex[, deleteCount[, item1]]);`
- startIndex : origin 0 , negative will begin that many elements from the end of the array.
- deleteCount : 0 or negetive, no elements are removed.

---

#### Array.prototype.sort()

- `arr.sort([func])`
- 함수 없으면 Unicode에 의해 정렬된다! (숫자도 문자로 바꿔서)
- 리턴 : 정렬된 배열! (새로운 카피 배열 아님)
- sorts the elements of an array **in place** and returns the array.

**`compareFunction(a, b)`이 있는경우**
- 결과값이 0보다 작으면, a를 b보다 앞으로 정렬
- 결과값이 0이면, a, b는 서로 바뀌지 않는다 - 보장되지 않는다.
- 결과값이 0보다 크면 b가 a앞으로 정렬

---

#### Array.prototype.forEach()

- executes a provided function once for each array elements
- `arr.forEach(function callback(currentValue[, index[, array]]) { //}[, thisArg])`;


---

#### Array.prototype.map()

- creates a new array.(length is the same)

```js
var numbers = [1, 4, 9];
var doubles = numbers.map(function(num) {
  return num * 2;
});

// doubles is now [2, 8, 18]
// numbers is still [1, 4, 9]
```
---


#### Array.prototype.filter()

- create a new array with all elements that pass the test.

```js
function isBigEnough(value) {
  return value >= 10;
}

var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// filtered is [12, 130, 44]
```

---


#### Array.prototype.reduce()

- `arr.reduce(callback[, initialValue])`
- accumulator(축적하는 값) : 콜백 결과값을 축적한다.

```js
var sum = [0, 1, 2, 3, 4].reduce(function (accumulator, currentVal) {
  return accumulator + currentVal;
}, 0);
// 0 = start value
// currentIndex : 1, 2, 3, 4
// accumulater  : 0, 1, 3, 6
// currentVal   : 1, 2, 3, 4
// return value : 1, 3, 6, 10  
```

---

#### Array.prototype.some()

- `arr.some(callback)`
- test whether at least one element in the array passes the test.
- returns boolean


---

#### Array.prototype.every()

- tests whether all elements in the array pass the test
- returns boolean value

---

#### Array.prototype.find()

- returns the value of the first element in the array that satisfies the provided testing function.
---

