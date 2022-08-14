>####     ES5와 ES6의 대표적인 차이
- 템플릿 리터럴
- 화살표 함수
- this
- let, const
- 모듈
- 클래스
<br/>
<br/>

>#### 1. 템플릿 리터럴
**백틱(`)**으로 문자열을 감싸 표현하는 기능
템플릿 리터럴을 사용하면 플레이스 홀더(**${variable}**)를 사용하여 백틱 내부에 문자열과 함께 표현식을 넣을 수 있다.
```js
var name = "현진";
var age = 25;
console.log(`저의 이름은 ${name}이고, 나이는 ${age}살 입니다.`);
```

>#### 2. 화살표 함수
화살표 함수로 함수 선언법이 좀 더 간단해졌다.
```js
var str = (arg1, arg2) => {
  console.log("용민");
};
```
```js
//화살표 함수에 인자(argument)가 하나밖에 없다면 괄호를 생략할 수 있다.
var str = arg1 => console.log(arg1);
```

>#### 3. this
ES6에서의 this 는 자신을 둘러싸고 있는 this를 바라보기 때문에 따로 바인딩이나 변수에 담을 필요 없다.

>#### 4. let, const
ES5에선 var 밖에 존재하지 않았다. ES6에서 let, const 추가   
- var 는 변수를 선언할 때 사용되는 키워드로, 재할당과 재선언에 굉장히 자유롭다. (나중에 값이 바뀌게 될 가능성이 큼)   
- let은 한번 선언된 변수에 동일한 이름으로 선언할 수 없다.   하지만, 값은 재할당 할 수 있다.   
- const는 한번 초기화된 변수에 재할당/재선언할 수 없다.   
- let, const는 블록레벨스코프!

>#### 5. module
ES5 이전에는 각 기능별로 JS 파일을 나누고 개발 및 관리하는 것이 불가능했다.   
ES6 부터는 import/export 로 모듈을 관리할 수 있다.

>#### 6. class
ES5에선 class라는 키워드는 없었지만 프로토타입을 통해 실현 가능했다.   
ES6에서는 class 키워드를 사용해서 선언할 수 있다.   
<br/>
<br/>

Reference) https://doozi0316.tistory.com/entry/JavaScript-ECMAScript%EB%9E%80-ES5%EC%99%80-ES6%EC%9D%98-%EC%B0%A8%EC%9D%B4var-const-let-%ED%99%94%EC%82%B4%ED%91%9C-%ED%95%A8%EC%88%98-class
