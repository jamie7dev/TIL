### JavaScript에 대해 더 공부하기

>🐤 JavaScript의 자료형과 JavaScript만의 특성은 무엇일까 ?

- 느슨한 타입(loosely typed)의 동적(dynamic) 언어 (Javascript의 변수는 어떤 특정 타입과 연결되지 않으며 모든 타입의 값으로 할당 및 재할당이 가능하다)

- JavaScript 형변환
  Javascript는 타입이 매우 유연한 언어.
  - 숫자형 Number()
  - 정수형 숫자 parseInt()
  - 부동 소수점의 숫자 parseFloat()
  - 문자형 String()
  - 주어진 값을 문자열로 변환 후 반환 toString()
  - 반올림하여 소수점 표현 toFixed()
  - 불리언 Boolean()

- ==, ===
  - ``=`` : 대입 연산자
  ```js
  var a = 1;
  let b = 3;
  const c = '5';
  ```
  - ``==`` : 동등 연산자(coercive). 강제 형 변환 후 값을 비교한다.
  ```js
  var a = 3;
  var b = '3'; //문자열
  let c = 3;
  a == b //true
  a == c //true
  b == c //true
  ```
  - ``===`` : 일치 연산자(strict equality). 강제 형변환 과정 없는 엄격한 비교
  ```js
  var a = 3;
  var b = '3'; //문자열
  let c = 3;
  a == b //false
  a == c //true
  b == c //false
  ```
  그럼 '=='만 사용하면 되는 것 아닌가?  
  => 원하지 않는 값 체크가 발생해도 판별하기 어렵기 때문에 확실한 비교가 보장되는 '==='를 쓰는 것이 좋다.
  
- 느슨한 타입(loosely typed)의 동적(dynamic) 언어의 문제점은 무엇이고 보완할 수 있는 방법에는 무엇이 있을지 생각해보세요.  
  느슨한 타입은 타입 없이 변수를 선언하는 것이다.
  ```
  /* JavaScript Example (loose typing) */
  var a = 13; // Number 선언
  var b = "thirteen"; // String 선언

  /* Java Example (strong typing) */
  int a = 13; // int 선언
  String b = "thirteen"; // String 선언
  ```
  ``java``는 숫자면 int로 선언하고 문자면 string으로 선언해야 하는데 ``javascript``는 느슨해서 편하구나~🍔  
    
  문제점은 대형 프로젝트나 협업 시 타입이 올바른지 체크하는 것이 매우 까다롭기 때문에 배포 시 예상치 못한 문제가 발생할 수 있다고 한다.  
  보완 -> Javascript의 단점을 보완하여 정적 타입 체크와 강력한 문법을 추가한 ``TypeScript``를 사용하면 된다고 함.
  🍑타입스크립트 배워야겠네? ㅎㅎ...  
  
- undefined와 null의 미세한 차이들을 비교해보세요  
  - ``undefined``: '아무 값도 할당받지 않은 상태'  
    var로 선언한 변수는 암묵적으로 undefined로 초기화된다.  
    변수를 참조했을 때 undefined가 반환된다면 선언 이후 값이 할당되지 않은 것.  
    그럼 변수에 값이 없다는 걸 나타내고 싶으면 어떻게 할까? => ``null``을 할당하면 된다!    
  
  - ``null``: '비어 있는, 존재하지 않는 값' (값의 부재)를 의미  
    변수에 null을 할당하는 것은 이전에 할당되어 있던 값에 대한 참조를 명시적으로 제거하는 것.  
  
  
  

>🐤 JavaScript 객체와 불변성이란 ?


- 기본형 데이터와 참조형 데이터
  - Primative Type(기본형 데이터 / 원시값)
    객체가 아닌 데이터 유형을 말한다.
    - Number
    - String
    - Boolean
    - Symbol(ES6에 추가, 객체 속성을 만드는 데이터 타입)
    - null
    - undefined

    기본형 데이터는 값을 그대로 할당한다.  
    메모리상에 고정된 크기로 저장되며 원시 데이터 값 자체를 보관하므로, 불변적이다.  
    기본적으로 같은 데이터는 하나의 메모리를 사용한다.(재사용)    
    
   - Reference Type
      참조 타입은 변수에 할당할때 값이 아닌 데이터의 주소를 저장한다.
      - Object
      - Array
      - Function RegExp (문자열에 나타나는 특정 문자조합가 대응시키기 위한 패턴)
      - Map 등
      참조형은 기본형 데이터의 집합이다. 참조형 데이터는 값이 지정된 주소값을 할당한다.


- JavaScript 형변환
  ?
  
- 불변 객체를 만드는 방법
  - ``불변 객체``란? 
    '변하지 않는 객체'
    즉, 이미 할당된 객체가 변하지 않는다는 뜻.
    
  1. ``const``
    const는 변수를 상수로 선언할 수 있다.  
    일반적으로 상수로 선언된 변수는 값을 바꾸지 못하는 것으로 알려져 있음.  (재할당 불가능)
    
  2. ``Object.freeze()``
    Javascript에서 기본적으로 제공하는 메소드. "객체를 동결하기 위한 메소드"
    
    ```js
    let test = {
        name : 'kim'
    }
    Object.freeze(test);
    test.name = 'Jung';
    console.log(test) // {name: 'kim'} 'Jung'으로 바뀌지 않음.    
    ```
    ```js
    but, Object.freeze()는 객체의 재할당은 가능!
    test = {
        age : 15
    };
    console.log(test); // {age: 15} <- 재할당 됨.
    ```
    
    따라서 불변 객체는 const와 Object.freeze()를 조합해서 만들 수 있음.  
    ``(const의 재할당불가 + Object.freeze()의 객체속성 변경불가)``
    
    ```js
    const test = {
        'name' : 'jung'
    };
    ```

    Object.freeze(test);
    먼저 const키워드로 바인딩 된 변수를 상수화 시킨 다음, Object.freeze()로 해당 변수를 동결 객체를 만들면
    객체의 재할당과 객체의 속성 둘 다 변경불가능한 불변 객체가 된다.

- 얕은 복사와 깊은 복사  
      원시값은 값을 복사 할 때 복사된 값을 다른 메모리에 할당 하기 때문에 원래의 값과 복사된 값이 서로에게 영향을 미치지 않는다
      
      ```js
      const a = 1;
      let b = a;

      b = 2

      console.log(a); //1
      console.log(b); //2
      ```
      
      참조값은 변수가 객체의 주소를 가리키는 값이기 때문에 복사된 값(주소)이 같은 값을 가리킨다.  
      
      ```js
      const a = {number: 1};
      let b = a;

      b.number = 2

      console.log(a); // {number: 2}
      console.log(b); // {number: 2}
      ```  
      
      이런한 객체의 특징 때문에 객체를 복사하는 방법은 크게 두가지로 나뉜다.  
      1. ``얕은 복사(Shallow Copy)``
      </br>
        바로 아래 단계의 값만 복사하는 방법 
        얕은 복사란 객체를 복사할 때 위의 예제처럼 원래값과 복사된 값이 같은 참조를 가리키고있는 것을 말한다.  
        객체안에 객체가 있을 경우 한개의 객체라도 원본 객체를 참조하고 있다면 이를 얕은 복사라고 한다.



      2. ``깊은 복사(Deep Copy)``
      </br>
        내부의 모든 값들을 하나하나 찾아서 전부 복사하는 방법
        깊은 복사된 객체는 객체안에 객체가 있을 경우에도 원본과의 참조가 완전히 끊어진 객체를 말한다.

 </br>
 </br>
 </br>
 </br>
 </br>
>🐤 호이스팅과 TDZ는 무엇일까 ?


- 스코프, 호이스팅, TDZ
  1. ``Scope``
   '변수에 접근할 수 있는 범위' / '변수를 찾기 위한 규칙'   
  - 블록 레벨 스코프; 코드 블록 ``{}``내에서만 참조(접근) 가능한 범위   
  - 함수 레벨 스코프; 함수 코드 블록 내에서만 참조(접근) 가능한 범위   
                ES6부터 let을 사용하면 블록 레벨 스코프를 사용할 수 있다.   
  - 렉시컬 스코프
  - 동적 스코프

  대부분의 C기반 언어들은 블록 레벨 스코프를 따른다.     
  하지만 Javascript는 함수 레벨 스코프를 따른다.   
  
  Scope의 종류
  <br/>
    1. 전역 스코프 (Global scope)
      전역에 변수를 선언하면 어디서든지 참조할 수 있는 전역 스코프를 갖는 변수가 된다.   
    2. 지역 스코프 (Local scope / Function-level scope)   
      함수 레벨 스코프라고도 할 수 있음.     
      함수 내에서 선언된 매개변수와 변수는 함수 외부에서는 유효하지 않음.   
    
    ```js
    var global = 'global'; //이렇게 전역에 선언하면
    
    function foo() {
    var local = 'local';    //지역 스코프
    console.log(global);    //어디서나 참조가 되고
    console.log(local);
    }
    foo();
    
    console.log(global);    //global
    console.log(local);     // Uncaught ReferenceError: local is not defined 에러가 난다.
    ```
    <br/>
 2. ``hoisting``   
 <br/>
  "변수의 선언과 초기화를 분리한 후, 선언만 코드의 최상단으로 옮기는 것"   
  코드가 실행하기 전 변수선언/함수선언이 해당 스코프의 최상단으로 끌어 올려진 것 같은 현상을 말한다.   
  인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것을 의미합니다.     
  var로 선언한 변수의 경우 호이스팅 시 undefined로 변수를 초기화합니다.     
  반면 let과 const로 선언한 변수의 경우 호이스팅 시 변수를 초기화하지 않습니다.  
  <br/>
  ------------호이스팅도 나중에 더 공부하기-------------
  
  
 4. ``TDZ``
  "Temporal Dead Zone"   
  변수 선언 전에 접근할 수 없는 것
  
  
  
<img width="600" alt="스크린샷 2022-08-09 오후 10 56 36" src="https://user-images.githubusercontent.com/104494969/183667807-eaf72101-3bfa-41cf-a340-3894cecfcb76.png">

- 함수 선언문과 함수 표현식에서 호이스팅 방식의 차이
  - 함수 선언문(function declartion) : 함수명이 정의되어 있고, 별도의 할당 명령이 없는 것
  ```js
  function sum(a,b) {
      return a + b;
  }
  ```

  - 함수 표현식 (function Expression) : 정의한 function을 별도의 변수에 할당하는 것
  ```js
  const sum = function(a,b) {
      return a + b;
  }
  ```
  
  - **호이스팅 방식의 차이**
    - 함수 선언식은 함수 전체를 호이스팅한다. 정의된 범위의 맨 위로 호이스팅되서 함수 선언 전에 함수를 사용할 수 있다는 것.
    - 함수 표현식은 별도의 변수에 할당하게 되는데, 변수는 선언부와 할당부를 나누어 호이스팅 하게 된다. 선언부만 호이스팅하게 된다.
  

- 실행 컨텍스트와 콜 스택

  - Execution Context(실행 컨텍스트)란?
  자바스크립트 엔진이 코드를 실행하기 위해선 코드에 대한 정보들이 필요합니다.   
  코드에 선언된 변수와 함수, 스코프, this, arguments 등을 묶어, 코드가 실행되는 위치를 설명한다는 뜻의 Execution Context라고 부릅니다.   
  자바스크립트 엔진은 Execution Context를 객체로 관리하며 코드를 Execution Context 내에서 실행합니다.
  
  - Execution Context의 관리: CallStack
    js 엔진은 생성된 Context를 관리하는 목적의 Call Stack(호출스택)을 갖고 있습니다.   
    JS는 단일 스레드 형식이기 때문에 런타임에 단 하나의 Call Stack이 존재합니다.   
    js 엔진은 전역 범위의 코드를 실행하며 Global Execution Context를 생성해 stack에 push합니다.   
    그리고 함수가 실행 또는 종료 될 때마다 Global Execution Context의 위로 Functional Execution Context stack을 push(추가), pop(제거)합니다.
</br>
    
    - Call Stack은 최대 stack 사이즈가 정해져있습니다.   
    Call Stack에 쌓인 Context Stack이 최대치를 넘게 될 경우 ‘RangeError: Maximum call stack size exceeded’라는 에러가 발생합니다.   
    이 에러는 Stack Overflow라고 부르기도 합니다.

![Context-Stack](https://user-images.githubusercontent.com/104494969/183912933-242ea59e-09b7-4ca8-9a9f-30fc5e7288f2.gif)   
</br>
    1. 코드의 전역 범위가 실행되며 Global Execution Context를 push합니다.   
    2. fn1이 실행됩니다.   
    3. fn1의 Functional Execution Context가 Call Stack에 push됩니다.      
    4. fn2이 실행됩니다.   
    5. fn2의 Functional Execution Context가 Call Stack에 push됩니다.   
    6. console.log가 실행됩니다.   
    7. console.log의 Functional Execution Context가 Call Stack에 push 됩니다.   
    8. console.log의 실행이 완료되며 console.log의 Functional Execution Context가 pop됩니다.   
    9. fn2의 실행이 완료되며 fn2의 Functional Execution Context가 pop됩니다.   
    10. fn1의 실행이 완료되며 fn1의 Functional Execution Context가 pop됩니다.   
    11. 앱 종료 시 Global Execution Context가 pop됩니다.   
</br>
</br>
- 스코프 체인(Scope Chain)

     
    스코프는 함수의 중첩에 의해 계층적 구조를 가진다.   

    변수를 참조할 때, 자바스크립트 엔진은 스코프 체인을 통해 변수를 참조하는 코드의 스코프에서 시작하여 상위 스코프로 이동하면서 선언된 변수를 검색한다.   

    스코프 체인은 outerEnvironmentReference와 밀접한 관계를 가진다.   

    💡 스코프 체인은 실행 컨텍스트의 렉시컬 환경을 '단방향'으로 연결한 링크드 리스트   
    
![image](https://user-images.githubusercontent.com/104494969/183913406-350f243a-e7e1-44b9-bc0f-40e4e0b229c6.png)


- 변수 은닉화 (variable shadowing)

    여러 스코프에서 동일한 식별자를 선언한 경우, 무조건 스코프 체인 상에서 가장 먼저 검색된 식별자에만 접근이 가능하다.
    ```js
    (function s(){
    let a = 'hi'
    })() //a is not defined
    ```
    즉, 직접적으로 변경되면 안되는 변수에 대한 접근을 막는것이다.

     ```js
     function hello(name) {
        let _name = name;
        return function () {
          console.log('Hello, ' + _name);
        };
      }

      let a = new hello('영서');
      let b = new hello('아름');

      a() //Hello, 영서
      b() //Hello, 아름
      ```
      이렇게 a와 b라는 클로저를 생성하면 함수 내부적으로 접근이 가능하다.
