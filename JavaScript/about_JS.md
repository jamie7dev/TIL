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
      1. 얕은 복사(Shallow Copy)
        얕은 복사란 객체를 복사할 때 위의 예제처럼 원래값과 복사된 값이 같은 참조를 가리키고있는 것을 말한다.  
        객체안에 객체가 있을 경우 한개의 객체라도 원본 객체를 참조하고 있다면 이를 얕은 복사라고 한다.



      2. 깊은 복사(Deep Copy)
        깊은 복사된 객체는 객체안에 객체가 있을 경우에도 원본과의 참조가 완전히 끊어진 객체를 말한다.


-----------나중에 더 깊게 알아보자---------------
