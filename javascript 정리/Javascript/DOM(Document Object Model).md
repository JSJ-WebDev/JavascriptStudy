
### DOM의 구성

1. **노드(Nodes)**:
   - **노드의 종류**: DOM 트리의 각 객체를 의미하며, 여러 종류의 노드가 존재한다.
     - **엘리먼트 노드(Element Nodes)**: HTML 태그로 구성된 노드이다. 예를 들어, `<div>`, `<p>` 같은 태그들은 모두 엘리먼트 노드이다.
     - **텍스트 노드(Text Nodes)**: 요소 내의 텍스트를 나타내는 노드이다.
     - **어트리뷰트 노드(Attribute Nodes)**: HTML 요소의 속성을 나타내는 노드이다.
     - **주석 노드(Comment Nodes)**: 주석을 나타내는 노드이다.
   
2. **요소(Elements)**:
   - 요소는 노드의 한 종류로, 주로 HTML 태그를 의미한다. 모든 HTML 태그는 엘리먼트 노드로 표현된다.
   - 요소는 문서 내에서 특정 역할을 수행하며, 각각의 요소는 고유한 속성과 메서드를 가질 수 있다.

### 요소와 노드의 차이점

- **노드**는 DOM 트리의 모든 객체를 의미하지만, **요소**는 HTML 태그를 나타내는 노드의 한 종류이다.
- **요소 노드**는 `<div>`, `<span>`, `<p>`와 같은 HTML 태그를 의미하며, 이는 문서의 구조를 정의한다.
- **텍스트 노드**는 요소 내의 텍스트를 포함하며, `<div>Hello</div>`에서 "Hello"는 텍스트 노드이다.
- **어트리뷰트 노드**는 요소의 속성을 나타내며, `<div id="myDiv"></div>`에서 `id="myDiv"`는 어트리뷰트 노드이다.

### 요소의 특수 속성과 메서드

- **특수 속성과 메서드**: 요소와 상호작용하기 위한 다양한 속성과 메서드가 있다. 예를 들어, `innerHTML`, `textContent`, `style` 등이 있다.
- **사용 가능한 메서드와 속성**: 요소의 종류에 따라 사용할 수 있는 메서드와 속성이 다르다. 예를 들어, `<img>` 요소는 `src` 속성을 가지며, `<a>` 요소는 `href` 속성을 가진다.
- **자바스크립트를 통한 선택**: 자바스크립트를 사용하여 다양한 방법으로 요소를 선택할 수 있다.
  - `getElementById(id)`: 특정 `id`를 가진 요소를 선택한다.
  - `getElementsByClassName(className)`: 특정 클래스를 가진 모든 요소를 선택한다.
  - `getElementsByTagName(tagName)`: 특정 태그 이름을 가진 모든 요소를 선택한다.
  - `querySelector(selector)`: CSS 선택자를 사용하여 일치하는 첫 번째 요소를 선택한다.
  - `querySelectorAll(selector)`: CSS 선택자를 사용하여 일치하는 모든 요소를 선택한다.
- **생성 및 제거**: 자바스크립트를 사용하여 요소를 생성하고 제거할 수 있다.
  - `createElement(tagName)`: 주어진 태그 이름을 가진 새로운 요소를 생성한다.
  - `remove()`: 선택한 요소를 DOM 트리에서 제거한다.
  - `appendChild(node)`: 특정 부모 요소의 자식으로 주어진 노드를 추가한다.
  - `insertBefore(newNode, referenceNode)`: 주어진 새로운 노드를 참조 노드 앞에 삽입한다.
  - `replaceChild(newNode, oldNode)`: 특정 부모 요소의 자식 요소를 새로운 요소로 교체한다.

### 예제 코드

다음은 자바스크립트를 사용하여 요소를 생성하고, 추가하고, 제거하는 예제 코드이다.

```html
<!DOCTYPE html>
<html>
<head>
    <title>DOM 조작 예제</title>
</head>
<body>
    <div id="content">
        <p>원래 내용</p>
    </div>
    <button id="changeButton">내용 변경</button>
    <button id="addButton">요소 추가</button>
    <button id="removeButton">요소 제거</button>

    <script>
        const contentDiv = document.getElementById('content');
        const changeButton = document.getElementById('changeButton');
        const addButton = document.getElementById('addButton');
        const removeButton = document.getElementById('removeButton');

        // 내용 변경
        changeButton.addEventListener('click', function() {
            contentDiv.innerHTML = '<p>변경된 내용</p>';
        });

        // 요소 추가
        addButton.addEventListener('click', function() {
            const newElement = document.createElement('p');
            newElement.textContent = '새로운 요소';
            contentDiv.appendChild(newElement);
        });

        // 요소 제거
        removeButton.addEventListener('click', function() {
            const elementToRemove = contentDiv.querySelector('p');
            if (elementToRemove) {
                elementToRemove.remove();
            }
        });
    </script>
</body>
</html>
```

위 예제에서는 버튼을 클릭하여 `<div>` 요소의 내용을 변경하고, 새로운 `<p>` 요소를 추가하고, 첫 번째 `<p>` 요소를 제거한다.

## Attribute VS Property

어트리뷰트(Attribute)와 프로퍼티(Property)는 자바스크립트에서 HTML 요소를 다룰 때 자주 혼동되는 개념이지만, 서로 다른 의미와 용도를 가진다. 다음은 어트리뷰트와 프로퍼티의 차이를 설명한 것이다.

### 어트리뷰트(Attribute)

- **정의**: 어트리뷰트는 HTML 요소의 시작 태그에 정의된 속성이다. 예를 들어, `<input type="text" id="username" value="JohnDoe">`에서 `type`, `id`, `value`는 모두 어트리뷰트이다.
- **역할**: 어트리뷰트는 HTML 문서에서 요소의 초기 상태를 설정하는 데 사용된다.
- **접근 방법**: 자바스크립트에서 어트리뷰트에 접근하거나 변경할 때는 `getAttribute`와 `setAttribute` 메서드를 사용한다.
- **예제**:
  ```javascript
  const inputElement = document.querySelector('input');
  const value = inputElement.getAttribute('value'); // "JohnDoe"
  inputElement.setAttribute('value', 'JaneDoe');
  ```

### 프로퍼티(Property)

- **정의**: 프로퍼티는 HTML 요소의 자바스크립트 객체 표현에서의 속성이다. HTML 요소는 브라우저에 의해 자바스크립트 객체로 변환되며, 이 객체의 속성이 프로퍼티이다.
- **역할**: 프로퍼티는 요소의 현재 상태를 나타내며, 동적으로 변경될 수 있다.
- **접근 방법**: 자바스크립트에서 프로퍼티에 접근하거나 변경할 때는 점 표기법 또는 대괄호 표기법을 사용한다.
- **예제**:
  ```javascript
  const inputElement = document.querySelector('input');
  const value = inputElement.value; // "JohnDoe"
  inputElement.value = 'JaneDoe';
  ```

### 주요 차이점

1. **초기화 vs. 현재 상태**:
   - 어트리뷰트는 요소의 초기 상태를 설정하며, HTML 문서에서 정의된 값이다.
   - 프로퍼티는 요소의 현재 상태를 나타내며, 자바스크립트에 의해 동적으로 변경될 수 있다.

2. **접근 및 변경 방법**:
   - 어트리뷰트는 `getAttribute`와 `setAttribute` 메서드를 사용하여 접근하고 변경한다.
   - 프로퍼티는 점 표기법(`element.property`)이나 대괄호 표기법(`element['property']`)을 사용하여 접근하고 변경한다.

3. **동기화**:
   - 일부 어트리뷰트와 프로퍼티는 동기화된다. 예를 들어, `id`, `class`와 같은 어트리뷰트는 해당 프로퍼티와 동기화되어 값을 공유한다.
   - 하지만 모든 어트리뷰트와 프로퍼티가 동기화되는 것은 아니다. 예를 들어, `value` 어트리뷰트는 요소의 초기 값을 설정하며, `value` 프로퍼티는 현재 값을 나타낸다. 사용자가 입력 필드에 값을 입력하면 `value` 프로퍼티는 변경되지만, 어트리뷰트의 값은 그대로 남아있다.

### 예제

다음은 어트리뷰트와 프로퍼티의 차이를 보여주는 예제이다.

```html
<!DOCTYPE html>
<html>
<head>
    <title>어트리뷰트와 프로퍼티의 차이</title>
</head>
<body>
    <input type="text" id="username" value="JohnDoe">
    <button id="changeValue">Change Value</button>
    <button id="logValue">Log Value</button>

    <script>
        const inputElement = document.getElementById('username');
        const changeValueButton = document.getElementById('changeValue');
        const logValueButton = document.getElementById('logValue');

        changeValueButton.addEventListener('click', () => {
            // 프로퍼티 값을 변경
            inputElement.value = 'JaneDoe';
            // 어트리뷰트 값을 변경
            inputElement.setAttribute('value', 'JaneDoe');
        });

        logValueButton.addEventListener('click', () => {
            console.log('Attribute value:', inputElement.getAttribute('value')); // 어트리뷰트 값 로그
            console.log('Property value:', inputElement.value); // 프로퍼티 값 로그
        });
    </script>
</body>
</html>
```

이 예제에서 `input` 요소의 초기 값은 어트리뷰트 `value`에 의해 설정된다. "Change Value" 버튼을 클릭하면, 자바스크립트로 프로퍼티와 어트리뷰트 값을 모두 "JaneDoe"로 변경한다. "Log Value" 버튼을 클릭하면 현재의 어트리뷰트 값과 프로퍼티 값을 로그로 출력한다.

이렇게 어트리뷰트와 프로퍼티는 HTML 요소를 다루는 데 있어 중요한 개념으로, 각각의 역할과 접근 방법이 다르다. 이를 이해하면 자바스크립트를 통해 더욱 정교하게 웹 페이지를 조작할 수 있다.

### DOM과 CSS 선택자

DOM(Document Object Model)은 HTML 문서의 구조화된 표현을 제공하는 프로그래밍 인터페이스이다. 이 인터페이스를 사용하면 자바스크립트로 문서의 요소에 접근하고 조작할 수 있다. DOM은 문서를 트리 구조로 표현하며, 이 트리의 각 노드는 문서의 일부를 나타낸다.

### CSS 선택자 요약

CSS 선택자는 HTML 문서 내에서 특정 요소를 선택하기 위해 사용되는 규칙이다. 자주 사용하는 선택자 몇 가지를 소개할게.

1. **id 선택자 (`#`)**:
   - 문법: `#id`
   - 설명: `id` 속성이 특정 값과 일치하는 요소를 선택한다.
   - 예제:
     ```javascript
     const element = document.querySelector('#myId');
     ```
     ```html
     <div id="myId">Hello</div>
     ```
     여기서 `id`가 `myId`인 요소를 선택하는 것이다.

2. **클래스 선택자 (`.`)**:
   - 문법: `.class`
   - 설명: `class` 속성이 특정 값과 일치하는 모든 요소를 선택한다.
   - 예제:
     ```javascript
     const element = document.querySelector('.myClass');
     ```
     ```html
     <div class="myClass">Hello</div>
     ```

3. **태그 선택자**:
   - 문법: `tag`
   - 설명: 특정 태그 이름을 가진 모든 요소를 선택한다.
   - 예제:
     ```javascript
     const element = document.querySelector('div');
     ```
     ```html
     <div>Hello</div>
     ```

4. **속성 선택자**:
   - 문법: `[attribute=value]`
   - 설명: 특정 속성값과 일치하는 요소를 선택한다.
   - 예제:
     ```javascript
     const element = document.querySelector('[type="text"]');
     ```
     ```html
     <input type="text">
     ```

### `querySelector` 메서드 사용 예제

- **id 선택자 사용 예제**:
  ```javascript
  const element = document.querySelector('#name');
  ```
  ```html
  <input id="name" type="text">
  ```
  여기서 `id`가 `name`인 `<input>` 요소를 선택한다.

- **클래스 선택자 사용 예제**:
  ```javascript
  const element = document.querySelector('.myClass');
  ```
  ```html
  <div class="myClass">Hello</div>
  ```
  여기서 클래스가 `myClass`인 첫 번째 `<div>` 요소를 선택한다.

- **태그 선택자 사용 예제**:
  ```javascript
  const element = document.querySelector('p');
  ```
  ```html
  <p>Paragraph</p>
  ```
  여기서 첫 번째 `<p>` 요소를 선택한다.

- **복합 선택자 사용 예제**:
  ```javascript
  const element = document.querySelector('div#content .item');
  ```
  ```html
  <div id="content">
    <div class="item">Item</div>
  </div>
  ```
  여기서 `id`가 `content`인 `<div>` 내에 있는 클래스가 `item`인 첫 번째 요소를 선택한다.

### DOM 조작 메서드

DOM을 조작하는 다양한 메서드들에 대해 알아보자. 이는 문서의 구조를 동적으로 변경할 수 있게 해준다.

1. **createElement(tagName)**:
   - 설명: 주어진 태그 이름을 가진 새로운 요소를 생성한다.
   - 예제:
     ```javascript
     const newDiv = document.createElement('div');
     ```
     새로운 `<div>` 요소를 생성한다.

2. **remove()**:
   - 설명: 선택한 요소를 DOM 트리에서 제거한다.
   - 예제:
     ```javascript
     const element = document.querySelector('#myId');
     element.remove();
     ```
     `id`가 `myId`인 요소를 제거한다.

3. **appendChild(node)**:
   - 설명: 특정 부모 요소의 자식으로 주어진 노드를 추가한다.
   - 예제:
     ```javascript
     const parent = document.querySelector('#parent');
     const newChild = document.createElement('div');
     parent.appendChild(newChild);
     ```
     `id`가 `parent`인 요소에 새로운 `<div>` 자식을 추가한다.

4. **insertBefore(newNode, referenceNode)**:
   - 설명: 주어진 새로운 노드를 참조 노드 앞에 삽입한다.
   - 예제:
     ```javascript
     const parent = document.querySelector('#parent');
     const newChild = document.createElement('div');
     const referenceChild = document.querySelector('#referenceChild');
     parent.insertBefore(newChild, referenceChild);
     ```
     `id`가 `referenceChild`인 요소 앞에 새로운 `<div>`를 삽입한다.

5. **replaceChild(newNode, oldNode)**:
   - 설명: 특정 부모 요소의 자식 요소를 새로운 요소로 교체한다.
   - 예제:
     ```javascript
     const parent = document.querySelector('#parent');
     const newChild = document.createElement('div');
     const oldChild = document.querySelector('#oldChild');
     parent.replaceChild(newChild, oldChild);
     ```
     `id`가 `oldChild`인 요소를 새로운 `<div>`로 교체한다.

### 결론

`querySelector` 메서드는 CSS 선택자를 사용하여 DOM 요소를 선택하는 강력한 도구이다. `#`은 id 선택자를 나타내며, 특정 `id`를 가진 요소를 선택하는 데 사용된다. 또한, DOM 조작 메서드인 `createElement`, `remove`, `appendChild`, `insertBefore`, `replaceChild` 등을 사용하면 문서의 구조를 동적으로 변경할 수 있다. 이를 통해 자바스크립트로 웹 페이지의 요소를 쉽게 접근하고 조작할 수 있다.