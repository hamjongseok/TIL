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

## 객체 반복문

- 배열은 저장된 데이터들이 순서를 가지고있지만 객체는 순서가없다. 키가 있고 벨류가 있을뿐이다.
- 그렇기에 일반적인 for문이 아니라 for / in 문 을 사용한다.

for / in 문

객체 뿐만 아니라 배열에서도 사용 가능하다.

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
