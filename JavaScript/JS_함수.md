# **🦄Java Script🦄**

## **함수**

---

## 함수 지향 - 유효범위

- 유효범위(Scope)는 변수의 수명을 의미한다.

```js
전역변수의 예시

var vscope = 'global';
function fscope(){
	alert(vscope);
}
fscope();

지역변수
var vscope = 'global'
function fscope(){
	var vscope = 'local'; //지역변수
	alert(vscope);
}
fscope();

위의 결과는 local이 된다. 자기자신에서 가장 가까운것을 호출하기때문.
```

지역변수

- 함수 내부에 변수를 지정하면 그 함수 내에서만 접근이 가능하다.
- var vscope 하면 지역변수 이다.
- var 을 지우게되면 로컬이아니라 전역변수를 의미하게된다.

전역변수

- 애플리케이션 전역에서 접근할수있는 변수

```js
var vsope = "global";
      function fscope() {
        vsope = "local";
      }
      fscope();
      alert(vsope);

이는 var를 붙이지않았기에 전역변수로써 local이 들어가게된다.

함수안에서만 해당한다. for문 등등 에서 var a = @@; 하게되면 전역변수로 취급한다.
```

정적 유효범위

```js
var i = 5;

function a() {
	var i = 10;
	b();
}

function b() {
	document.write(i);
}

a();

함수가 사용될때가 아닌 정의될때 이므로

a();는 5가 나온다.
```

---

## 함수지향 - 값으로서의 함수와 콜백

```js

for key in grades

grades라는 변수가 담겨져있는 그릇의 값들을 반복문이 실행할때마다 하나씩 가져와서
key에다가 key값을 담는다.
key는 for문 안에서 자동으로 생성된다.

for / in 문은 해당 객체의 모든 열거할 수 있는 프로퍼티를 순회 할수 있도록 해준다.
프로퍼티 -> 객체의 속성

for (변수 in 객체) {
        document.write("key : " + 변수 + " value : " + 객체[변수] + "<br />");
```

## this 변수

- javascript 예약어
- **this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수(self-reference variable)이다.**
- **this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다.**

```js
예시;

var grades = {
  list: { egoing: 10, k9905: 8, sorialgi: 80 },
  show: function () {
    alert(this.list);
  },
};
```

---

## 유효범위

유효범위(Scope)는 변수의 수명을 의미한다.

```js

전역변수의 예시

var vscope = 'global';
function fscope(){
	alert(vscope);
}
fscope();

지역변수
var vscope = 'global'
function fscope(){
	var vscope = 'local'; //지역변수
	alert(vscope);
}
fscope();

위의 결과는 local이 된다. 자기자신에서 가장 가까운것을 호출하기때문

```

### 지역변수

함수 내부에 변수를 지정하면 그 함수 내에서만 접근이 가능하다.

var vscope 하면 지역변수 이다.

var 을 지우게되면 로컬이아니라 전역변수를 의미하게된다.

### 전역변수

애플리케이션 전역에서 접근할수있는 변수

```js
var vsope = "global";
      function fscope() {
        vsope = "local";
      }
      fscope();
      alert(vsope);

이는 var를 붙이지않았기에 전역변수로써 local이 들어가게된다.

함수안에서만 해당한다. for문 등등 에서 var a = @@; 하게되면 전역변수로 취급한다.
```

### 정적 유효범위

```js

var i = 5; //전역변수

function a() {
	var i = 10; //지역변수
	b(); //호출
}

function b() {
	document.write(i); //출력
}

a();

함수안에서의 var i = 10 ; 은 지역변수 , 함수안에서만쓰는것 이므로
전역변수인 i에 영향을 주지않는다.

result :
a();는 5가 나온다.

```

---

### 값으로서의 함수

- 자바스크립트에서는 함수도 객체이다. 다시말해 일종의 값이다.
- javascrip의 함수가 다른 언어의 함수가 다른점은 함수가 값이 될수 있다는 점이다.

```js
function a() {}

두개는 같은 의미이다.
var a = function(){}


아래의 예시처럼 객체의 속성값으로 담겨진 함수를 메소드 (method)라고 부른다.

a = {
	b : function () {

}
};

쉽게 생각해서 객체안에 내장되어있는 함수를 메소드라고 하면되는것같다.

```

- 함수는 값이기때문에 다른 함수의 인자로 전달될수 있다.
- 이를 바로 **콜백함수**라고한다.
