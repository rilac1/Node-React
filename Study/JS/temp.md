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
`null`: object타입
`undefined`: 타입이 정해지지 않음 (초기화되지 않은 변수나 존재하지 않는 값)
```js
null==defined   // false
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
#### `for/in` `for/of`
- `for/in`: 해당 객체의 모든 열거할 수 있는(enumerable) **프로퍼티**를 순회
    ```js
    var obj = { name : "이순신", age : 20 };
    for (var i in obj) document.write(i + "<br>");
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
    arr.constructor // function Array() { [native code] }
    ```

## 6. 함수



