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
  java는 숫자면 int로 선언하고 문자면 string으로 선언해야 하는데 javascript는 편하구나~🍔  
    
  문제점은 대형 프로젝트나 협업 시 타입이 올바른지 체크하는 것이 매우 까다롭기 때문에 배포 시 예상치 못한 문제가 발생할 수 있다고 한다.  
  보완 -> Javascript의 단점을 보완하여 정적 타입 체크와 강력한 문법을 추가한 ``TypeScript``를 사용하면 된다고 함.
  🍑타입스크립트 배워야겠네? ㅎㅎ...  
  
- undefined와 null의 미세한 차이들을 비교해보세요  
  - ``undefined``: '아무 값도 할당받지 않은 상태'  
    var로 선언한 변수는 암묵적으로 undefined로 초기화된다.  
    변수를 참조했을 때 undefined가 반환된다면 선언 이후 값이 할당되지 않은 것.  
    그럼 변수에 값이 없다는 걸 나타내고 싶으면 어떻게 할까? => null을 할당하면 된다!    
  
  - ``null``: '비어 있는, 존재하지 않는 값' (값의 부재)를 의미  
    변수에 null을 할당하는 것은 이전에 할당되어 있던 값에 대한 참조를 명시적으로 제거하는 것.  
  
  
  
  
  
  