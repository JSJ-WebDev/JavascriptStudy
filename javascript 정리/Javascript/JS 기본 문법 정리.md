
---
## JavaScript 기본 문법

JavaScript는 웹 개발에서 가장 널리 사용되는 프로그래밍 언어 중 하나로, 웹 페이지에 동적 기능을 추가하는 데 사용된다. JavaScript의 기본 문법에 대한 설명을 통해 기초를 탄탄히 다져봅시다.

### 1. [[변수]] 선언

JavaScript에서는 변수를 선언하는 방법이 세 가지 있습니다: `var`, `let`, `const`.

- `var`: 함수 범위(function scope)를 가지며, 재선언과 재할당이 가능합니다.
- `let`: 블록 범위(block scope)를 가지며, 재선언은 불가능하지만 재할당은 가능합니다.
- `const`: 블록 범위(block scope)를 가지며, 재선언과 재할당이 모두 불가능합니다. 단, 객체의 속성은 변경할 수 있습니다.

```javascript
var x = 10;
let y = 20;
const z = 30;
```

### 2. 데이터 타입

JavaScript에는 여덟 가지 기본 데이터 타입이 있습니다.

- `Number`: 숫자형
- `String`: 문자열
- `Boolean`: 논리형 (true 또는 false)
- `Undefined`: 값이 정의되지 않음
- `Null`: 값이 비어 있음
- `Object`: 객체형
- `Symbol`: 고유하고 변경 불가능한 데이터 타입
- `BigInt`: 안전하게 정수를 표현할 수 있는 데이터 타입

```javascript
let number = 42;
let string = "Hello, World!";
let boolean = true;
let undefinedVar;
let nullVar = null;
let object = { name: "John", age: 30 };
let symbol = Symbol('symbol');
let bigInt = 1234567890123456789012345678901234567890n;
```

### 3. 연산자

#### 산술 연산자

- `+` (덧셈)
- `-` (뺄셈)
- `*` (곱셈)
- `/` (나눗셈)
- `%` (나머지)
- `**` (거듭제곱)

```javascript
let sum = 10 + 5; // 15
let difference = 10 - 5; // 5
let product = 10 * 5; // 50
let quotient = 10 / 5; // 2
let remainder = 10 % 3; // 1
let power = 2 ** 3; // 8
```

#### 비교 연산자

- `==` (값만 비교)
- `===` (값과 타입 모두 비교)
- `!=` (값만 비교, 다르면 true)
- `!==` (값과 타입 모두 비교, 다르면 true)
- `<`, `>`, `<=`, `>=` (작다, 크다, 작거나 같다, 크거나 같다)

```javascript
let isEqual = 5 == "5"; // true
let isStrictEqual = 5 === "5"; // false
let isNotEqual = 5 != "5"; // false
let isStrictNotEqual = 5 !== "5"; // true
let isLessThan = 5 < 10; // true
let isGreaterThan = 10 > 5; // true
```

### 4. NaN (Not-a-Number)

`NaN`은 "Not-a-Number"의 약자로, 수학적 연산 또는 숫자 변환이 실패했음을 나타내는 특수한 값입니다. `NaN`은 다음과 같은 경우에 발생할 수 있습니다:

- 숫자가 아닌 값을 숫자로 변환하려 할 때
- 유효하지 않은 수학적 연산을 수행할 때

```javascript
console.log(0 / 0); // NaN
console.log(Math.sqrt(-1)); // NaN
console.log(parseInt("hello")); // NaN
```

#### NaN의 특성

1. **유일함**: `NaN`은 JavaScript에서 자신과 일치하지 않는 유일한 값입니다. 즉, `NaN === NaN`은 `false`입니다.
2. **유형**: `NaN`은 기본적으로 `number` 타입입니다.

```javascript
console.log(NaN === NaN); // false
console.log(typeof NaN); // "number"
```

#### NaN 체크 방법

1. **isNaN() 함수**: 주어진 값이 `NaN`인지 확인합니다. 이 함수는 전달된 값이 숫자로 변환될 수 없는 경우에도 `true`를 반환합니다.
2. **Number.isNaN() 함수**: 주어진 값이 정확히 `NaN`인지 확인합니다. 더 엄격한 비교를 수행합니다.

```javascript
console.log(isNaN(NaN)); // true
console.log(isNaN("hello")); // true (문자열을 숫자로 변환하려다 실패했기 때문에)
console.log(Number.isNaN(NaN)); // true
console.log(Number.isNaN("hello")); // false (문자열은 NaN이 아니기 때문에)
```

#### NaN 사용 시 주의사항

- `NaN`은 오류를 나타내는 데 사용되므로, 연산 결과로 `NaN`이 발생하면 코드의 논리나 데이터의 유효성을 다시 확인해야 합니다.
- 특히 사용자 입력이나 외부 데이터 소스에서 숫자를 다룰 때 `NaN` 발생 가능성을 염두에 두고 예외 처리를 해야 합니다.

### 5. 조건문

#### if-else

```javascript
let age = 20;

if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

#### switch

```javascript
let fruit = "apple";

switch (fruit) {
    case "banana":
        console.log("Banana is yellow");
        break;
    case "apple":
        console.log("Apple is red");
        break;
    default:
        console.log("Unknown fruit");
}
```

### 6. 반복문

#### for

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i); // 0, 1, 2, 3, 4
}
```

#### while

```javascript
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```

#### do-while

```javascript
let i = 0;
do {
    console.log(i);
    i++;
} while (i < 5);
```

