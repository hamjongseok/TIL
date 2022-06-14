# **🦄Java Script🦄**

## **기본 개념**

---

웹브라우저라는 소프트웨어를 프로그래밍적인 제어하는 언어

→ 하지만 이젠 웹브라우저만을 제어하지 않는다. (탈웹브라우저화)

- 웹서버 (node.js) → 서버사이드 스크립트
- 웹서버에서 사용되는 대표적인 기술 php, java, python등등

웹브라우저 → 요청 웹 ← 응답 웹서버

자바스크립트를 이용하면 웹브라우저를 제어(vue, react), 웹서버를 제어(node.js) 할수있다.

탈웹 (구글 엑셀등) → 여러가지 환경에서 사용할수 있다.

세미콜론

- 자바스크립트에서는 줄바꿈으로 명령어가 끝났다고 알기때문에 세미콜론이 없어도 된다.
- 하지만 명시적으로 붙이는것을 습관화 해두는것이 좋다.
- 한줄에 명령어 하나일때는 세미콜론을 생략해도되지만 한줄에 두개의 명령어가있을때는 무조건 세미콜론을 붙여야한다.

---

## 숫자와 문자, 비교연산자

Math 사용 (수학관련된 명령들 모아둔 집합체)

```js
Math.pow(3,2)  => 제곱 (3의 2승)

Math.round(10.6) => 반올림 (11)

Math.ceil(10.2) => 가장 가까운 큰정수 (11)

Math.floor(10.2) => 가장 가까운 아래정수로 내린다(10)

Math.random() => 랜덤숫자를 계속 만들어줌 (이렇게하면 1보다 작은 실수만나옴)

100 * Math.random() => 100이하의 랜덤숫자

소수점을 없애려면

Math.round(100 * Math.random());
-> round의 반올림을 통해 소수점이 아닌 100이하의 정수만 나오게된다.
```

### 문자열

```js
문자열 끼리 더하고싶을때
alert("Hello" + " world");

"coding everybody".length -> 16

문자열의 길이를 반환해주는 함수
```

### 변수

- JavaScript에서는 변수를 `var`로 시작한다. 즉, var은 변수를 선언하겠다는 것을 의미한다.

---

## 비교

대입연산자 ( = )

동등연산자 ( == ) equal operator

일치 연산자 ( === ) strict equal operator

```js
strict => 엄격한

alert (1=='1'); //true

alert (1==='1'); //false

데이터의 형식도 일치할때만 true가 된다.

== 대신 ===을 쓰는것을 강력하게 권한다고한다.
```

## 일치 연산자의 몇가지 예시

```js
null -> 값이 없다
undefined -> 정의되어있지 않은

alert(null == undefined); //true

alert(null === undefined); //false
정의되지않음과 값이 없다라는 null을 엄격하게 비교하면 값이 다르다고 뜬다.


alert(true == 1); //true
alert(true === 1) //false

alert(0 === -0) //true

0은 양수건 음수건 똑같다

!==
!==는 !=와 ==의 관계는 같다
정확하게 같지 않다는 의미이다.
```

---

## 함수

함수(function)이란 ?

하나의 로직을 재실행 할수 있도록 하는것으로 코드의 재사용성을 높여준다.

함수의 형식

```js

function 함수명 ([인자 ...[, 인자]]){

	코드

	return (반환값);
}

예시

<script>
      function numbering() {
        document.write(1);
      } //함수 정의
      numbering();
</script>


다른 함수 선언방법

numbering = function(){
	i = 0;
	while (i < 10){
		dounment.write(i);
		i += 1;
	}
}


(function(){
	i = 0;
	while (i < 10){
		dounment.write(i);
		i += 1;
	}
})();

-> 함수 정의하고 바로 호출이 가능.
이는 익명함수라고 한다. (일회성 인경우 이렇게 사용하기도한다.)

```

## 입력함수

JavaScript 의 입력함수

- prompt()
  - 함수는 사용자에게 윈도우 창을 띄워 데이터를 입력받을 수 있는 함수

```js
<script>var a = prompt(); document.write(a);</script>;

prompt("윈도우창", "입력창");
```

## 출력함수

JavaScript 의 출력함수

```js


alert("확인을 누를 때까지 다른 작업을 할 수 없어요!");

window.alert() 메소드는 브라우저와는 별도의 대화 상자를 띄워 사용자에게 데이터를 전달해준다.



document.write('hello <br />');

document.write() 메소드는 웹 페이지가 로딩될 때 실행되면, 웹 페이지에 가장 먼저 데이터를 출력한다.

따라서 document.write() 메소드는 대부분 테스트나 디버깅을 위해 사용된다.



console.log(4 * 5);

웹 브라우저의 콘솔을 통해 데이터를 출력

```

---

## 배열

- 배열(array)란 연관된 데이터를 모아서 통으로 관리하기 위해 사용하는 데이터 타입이다.
- 변수가 하나의 데이터를 저장 하기 위한것이라면 배열은 여러개의 데이터를 하나의 변수에 변수에 저장하기 위한것이라고 할수있다.

```js

배열

var member = ['ham', 'jong', 'seok'];


배열 추가 방법

member.push ('han');

member = ['ham', 'jong', 'seok', 'han'];




복수의 원소를 배열에 추가하는방법

member = member.concat(['ddd','fff']);



배열의 시작점에 원소를 추가하는방법

member.unshift('z');

z,ham,jong,seok,ddd,fff <- 만들어짐



splice 함수

배열의 틀정 구간을 추출하거나 특정구간에 특정 배열을 추가한다.
(필요할때 찾아보기)


제거 함수
shift

var li = ['a', 'b', 'c', 'd'];

li.shift();

-> a 제거된다.

li.pop();
-> d , 마지막원소 제거


정렬함수

li.sort();

역순 정렬
li.reverse();


```

---

## Head

```js
c언어에서의 헤더파일 include부분을 js에서는 어떻게 하나 생각했었는데

 <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
	<script src="gree.js"></script>
    <title>Document</title>
  </head>

  html 헤더파일에 src 속성을 사용해서 include 시켜주면되었다.
```
