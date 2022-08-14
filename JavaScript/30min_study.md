> ### Object(객체)
**key와 value 쌍으로 이루어짐.**
```js
{"지역이름":"서울",
 "확진자수":5607,
 "사망자수":66
}
```
```js
//변수명과 그 안의 값을 key와 value로 쓰고 싶을 때
let x = 1, y = 2, z = 3
let object = {x, y, z}	//{x:1, y:2, z:3}
```
**Object도 수정 가능**
```js
- 추가: Object['hello'] = 'world'	//{x:1, y:2, z:3, hello:'world'}
- 삭제: delete object['hello'] //추천X, 메모리에는 남이 있음
	=> object['hello'] = null; //이렇게 하기!
```
**메서드**
```js
1. Object.keys()	//['x', 'y', 'z'] key값만 출력
2. Object.values()	//[1, 2, 3] value만 출력
3. Object.entries() // ['x', 1] ['y', 2] ['z', 3] array로 출력
```    

>### 조건문
- 삼항연산자
간단한 if문
```js
let result = true ? 1 : 100;	//1
```
- switch
조건문에 비교할 초이스가 많은 경우 가독성이 좋음
```js
switch(condition){
  case value1:			//조건=value1이면
    statement1;			//statemnet1 실행 후
    break;				//종료
  case value2:
    statement2;
    break;
  default:				//생략 가능
  	statement3;
}
```
- for문 중첩 (ex.구구단)
```js
for (let i = 1; i < 10; i++){
	for (let j = 1; j < 10; j++){
    	console.log(`${i}X${j}=${i*j}`)
    }
}
// 1X1=1
// ...
// 9X9=81
```
- for of (ex.모든 자릿수의 합)
안에 있는 요소들을 순회
```js
let s = 0;
let a = '19821';
for (let i of a) {
	s += parseInt(i)
}
//21
```

>### function(함수)
1. 함수 선언식: 호이스팅O
(호이스팅: 내용을 최상위로 올려주는 것)
```js
function add (x,y){
	return x + y;
}
//add를 문서 내 어디서나 사용 가능
```
2. 함수 표현식: 호이스팅X
(엄밀히 말하자면 호이스팅은 일어나지만, TDZ(Temporal Dead Zone, 일시적 사각지대)에 빠지게 됨)
```js
let add2 = function(x, y){
	return x + y;
}
//add2는 선언 전 위에서는 못 씀
```

>#### callback 함수
함수를 parameter로 주고 나중에 실행시키겠다는 뜻
(함수 내부에서 실행하는 함수)
```js
function cal(a, b){
	return a(10, 10) + b(10, 10);
}
cal((a, b) => a + b, (a, b) => a * b);
//120
```
흠... 이건 아직도 잘 이해가 안 간다;;

>#### Arrow fucntion(화살표 함수)
```js
function square(x){
	return x ** 2;
}
//위 함수를 화살표 함수를 사용하면
let square = x => x ** 2;
//이렇게 간단하게 표현할 수 있다.
```

> ### DOM
[Document Object Model]
브라우저가 HTML을 인식하는 방식을 계층화시켜 트리 구조로 만든 Object Model.
1. 웹 브라우저는 정적인 HTML 문서를 해석해서
2. 요소들을 트리 형태로 구조화한 문서(데이터)를 생성 = DOM을 생성
3. 화면에 해석한 결과를 보여주는 렌더링을 함.
![](https://velog.velcdn.com/images/jamie7dev/post/bcd121d3-e1da-44a1-8cf5-1a8a5a2cec0a/image.png)
- DOM을 쓰는 목적
HTML은 정적인 Text => 웹이 사용자와 동적으로 상호작용하려면 
Javascript를 사용해서 웹 콘텐츠를 추가, 수정, 삭제, 이벤트 처리 등을 하게 되는데 
JS로 작성하면 DOM에 그 결과가 반영되고 웹페이지가 다시 렌더링되는 그런 개념...


