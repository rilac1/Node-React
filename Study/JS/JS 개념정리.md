## 1-5. 자바 스크립트 출력
#### 1. `window.alert()` 메소드
```js 
<script>
function alertDialogBox() {
    alert("확인을 누를 때까지 다른 작업을 할 수 없어요!");
}
</script>
```
#### 2. HTML DOM 요소를 이용한 innerHTML 프로퍼티
```js
<script>
    var str = document.getElementById("text");
    str.innerHTML = "이 문장으로 바뀌었습니다!";
</script>
```
#### 3. `document.write()` 메소드
```js
<script>
    document.write(4 * 5);
</script>
```
#### 4. `console.log()` 메소드
```js
<p>F12를 눌러서 콘솔 화면을 열면 결과를 확인할 수 있습니다.</p>
<script>
    console.log(4 * 5);
</script>
```

## 2. 타입
#### `null` vs `undefined`
null과 undefined는 같은 의미이지만, 타입이 다름.
- `null`: object타입
- `undefined`: 타입이 정해지지 않음 (초기화되지 않은 변수나 존재하지 않는 값)
```js
null==undefined     // true
null===undefined    // false
```
#### `Number(str)` vs `parseInt(str)`
`parseInt(str)`는 문자열이 숫자로 시작하는 경우에는 숫자가 끝날 때까지만 형변환을 하여 num에 저장됨. 시작이 숫자가 아니면 Number()와 마찬가지로 NaN이 저장됨.
```js
var num = Number('1000원')          // NaN

var num = parseInt('1000원')        // 1000
var num = parseInt('가격:1000원')   // NaN
```

## 3. 연산자
#### `==` vs `===`
- 동등 연산자(`==`): 두 피연산자의 값이 서로 같으면 참 반환
- 일치 연산자(`===`): 두 피연산자의 값과 타입이 같아야만 참 반환
```js
var x = 3, y = '3', z = 3;
(x == y)        // true
(x === y)       // false
(x === z)       // true
```

#### typeof
자바스크립트는 타입을 알아낼 때 함수가 아닌 연산자를 사용한다.
```js
typeof value    // O
typeof(value)   // X
```

#### instance of
`instanceof` 연산자: 피연산자인 객체가 특정 객체의 인스턴스인지 아닌지를 확인
```js
var str = new String("이것은 문자열입니다.");
str instanceof Object;  // true
str instanceof String;  // true
str instanceof Array;   // false
```

#### void
`void` 연산자: 피연산자로 어떤 타입의 값이 오던지 상관없이 언제나 undefined 값만을 반환
```js
<a href="javascript:void(0)">이 링크는 동작하지 않습니다.</a>
```

## 4. 제어문
#### `for/in`, `for/of`
- `for/in`: 해당 객체의 모든 열거할 수 있는(enumerable) **프로퍼티**를 순회
    ```js
    var obj = {
        name : "이순신",
        age : 20 };
    for (var i in obj) document.write(i + "<br>");  // 이순신, 20
    ```
- `for/of`: 반복할 수 있는(iterable) **객체**를 순회
    ```js
    var arr = [3, 4, 5];
    for (var value of arr) document.write(value + " ");
    ```

## 5. 배열
#### 배열의 생성
```js
var arr = [1,2,3];
var arr = Array(1,2,3);
var arr = new Array(1,2,3); 
```

#### 배열요소의 추가
```js
arr.push('new');
arr[arr.length] = 'new';
arr[i] = 'new';     // 중간에 비어있는 요소는 undefined (희소 배열)
``` 

#### 배열 여부 확인
- 자바스크립트에서는 배열이라는 타입(type)을 별도로 제공하지 않는다.  
- 자바스크립트 배열은 객체(object) 타입이 되며, `typeof` 연산자를 사용하면 'object'를 반환한다.  
- 자바스크립트에서 해당 변수가 배열인지 여부를 확인하는 방법
  - `Array.isArray()` 메소드
  - `instanceof` 연산자
  - `constructor` 프로퍼티: 생성자 함수를 return
    ```js
    doucument.write(arr.constructor)    // function Array() { [native code] }
    ```

## 6. 함수
#### 값으로서의 함수
자바스크립트에서 함수는 문법적 구문일뿐만 아니라 값(value)이기도 하다.
따라서 함수가 변수에 대입될 수도 있으며, 다른 함수의 인수로 전달될 수도 있다.
```js
function sqr(x) {
    return x*x;
}
var sqrNum = sqr;
squrNum(2)      // 4
```

#### 변수의 유효범위
- 함수 내에서 전역변수를 선언하려면?
  - `var`키워드 없이 선언한다.
- 함수 내에서 전역변수와 같은 이름을 가진 변수가 선언되어 있을 때 전역변수에 접근하려면?
  - window.[변수명]으로 접근한다.

#### 함수 호이스팅
자바스크립트 함수 안에 있는 모든 변수의 선언은 함수의 맨 처음으로 이동된 것처럼 동작함
```js
var globalNum = 10;
function printNum() {
    document.write(globalNum+"<br>")    // 10이 아닌 출력될 것으로 예상.
    globalNum = 20;
    document.write(globalNum+"<br>")
}
// After hoisting
function printNum() {
    var globalNum;                      // 변수 선언 호이스팅됨.
    document.write(globalNum+"<br>")    // 10이 아닌 undefined 출력됨.
    globalNum = 20;
    document.write(globalNum+"<br>")
}
```

#### 매개변수와 인수
- 자바스크립트에서는 함수를 정의할 때는 매개변수의 타입을 따로 명시하지 않음 (인터프리터 언어 특징)
- 함수를 호출할 때 함수의 정의보다 적은 수의 인수가 전달될 경우 오류를 발생시키지 않고 나머지 매개변수에 undefined 값을 설정함

##### arguments 객체
arguments 객체는 함수가 호출될 때 전달된 인수를 배열의 형태로 저장하고 있음
```js
function addNum() {
    var sum = 0;
    for (var i; i<arguments.length; i++)
        sum += arguments[i];
    return sum;
}
```
> arguments 객체는 배열과 비슷할 뿐, 실제로 Array 객체는 아니다. 숫자로 된 인덱스와 length 프로퍼티만을 가지고 있을 뿐, 모든 것을 배열처럼 다룰 수는 없다.

#### 미리 정의된 전역함수
- `eval()`: 문자열로 표현된 자바스크립트 코드를 실행
    ```js
    var x = 10, y = 20;
    var a = eval("x + y"); // 30
    ```
- `isNaN()`: 전달된 값이 숫자가 아닌지
    ```js
    isNaN(123);      // false
    isNaN("123");    // false
    isNaN("abc");    // true
    isNaN(NaN);      // true
    ```
    `boolean` / `null` / 빈문자열(`""`) 모두 숫자로 취급. (단, undefined는 아님)
- `isFinite()`: 전달된 값이 유한한 수인지 아닌지
- `parseFloat()`: string to float
- `parseInt()`: string to int
- `encodeURI()`, `encodeURIComponent()`
    ```js
    var uri = "http://google.com/search.php?name=홍길동&city=서울";
    var enc1 = encodeURI(uri);
    var enc2 = encodeURIComponent(uri);
    // enc1: http://google.com/search.php?name=%ED%99%8D%EA%B8%B8%EB%8F%99&city=%EC%84%9C%EC%9A%B8
    // enc2: http%3A%2F%2Fgoogle.com%2Fsearch.php%3Fname%3D%ED%99%8D%EA%B8%B8%EB%8F%99%26city%3D%EC%84%9C%EC%9A%B8
    ```
- `decodeURI(), decodeURIComponent()`

## 7. 객체
