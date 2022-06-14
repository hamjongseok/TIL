# **🦄Java Script🦄**

## **객체**

---

- 객체도 배열과 같이 담는 그릇이다. 배열과의 가시적인 차이점은 배열은 index가 0 . 1. 2 숫자이고
- 객체는 내가 원하는대로 할수있다. (문자, 숫자 등)

- 객체 생성방법

```js

var grades = {'egoing': 10, 'k8805' : 6, 'sorialgi' : 80};

위의 예제에서 egoing은 key(index)가 되고 10은 value가 된다.
문자 -> 인덱스

배열과 만드는방법은 유사하지만 value가 존재하며 배열은 [ ] 객체는 { }


객체 생성 다른방법

var grades = {}; 빈객체를 생성
grades['egoing'] = 10;
grades['k8805'] = 6;
grades['sorialgi'] = 80;

['egoing'] ->인덱스이다.

var grades = new object(); <- 똑같은 의미이다.
grades['egoing'] = 10;
grades['k8805'] = 6;
grades['sorialgi'] = 80;

grades['egoing'];
return -> 10
grades.egoing;
return -> 10
같은 의미이다.

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
