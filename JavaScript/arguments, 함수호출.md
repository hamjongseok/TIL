# **🦄Java Script🦄**

## **arguments**

---

- arguments라는 객체이다.
- 함수안에서 그함수의 여러 정보를 담고있는 특히 인자와 관련된 정보를 담고있는 객체이다. 유사배열이라고도함

```js
function sum() {
        var i,
          _sum = 0;
        for (i = 0; i < arguments.length; i++) {
          document.write(i + ":" + arguments[i] + "<br />");
          _sum += arguments[i];
        }
        return _sum;
      }
      document.write("result : " + sum(1, 2, 3, 4));


근데 sum함수를 보면 () 매개변수가 없다.

매개변수와 인자의 차이
엄격하게 따진다며 인자를 값이라고부른다.  arg1(인자)
arg1 == 매개변수 파라미터  sum (arg1) 매개변수


근데 어떻게 들어오나?
자스는 매개변수가 3개인데 인자가 1개인경우에도 문제없고
매개변수가 0개인데 인자가 4개인경우에도 문제가없다.


arguments에 sum(1, 2, 3, 4) 인자 4개가 들어가있다.

그렇기 때문에 자스에서는 인자와 매개변수의 값이 달라도 에러를 발생시키지 않기때문에
개발자가 의도한 상황과 다르게 될수 있으므로
function.length;
arguments.length;

== 같은지 비교를 하고 != 같지않을경우에는 종료시킨다든지의 예외처리를 하면된다.
```

---

## 함수호출

```js

function func(){
}

func();

함수 기본적인 호출과 선언

함수는 일종의 객체이다.
객체는 속성을 가지고있다. 프로퍼티

그 속성에 함수가 들어있다면 메소드라고부른다.

func.apply
func.call

을할수있다. 이는 내장메소드이다.

sum(1,2);
sum.apply(null, [1,2]);

apply 메소드를 왜쓰는거지?

첫번째 인자 null이아니라 다른것을 사용할경우에 유용하기때문에 사용하는것이다.

예제

o1 = { val: 1, val2: 2, val3: 3 };
      o2 = { v1: 10, v2: 50, v3: 100, v4: 25 };
      function sum() {
        var _sum = 0;
        for (name in this) {
          _sum += this[name];
        }
        return _sum;
      }
      alert(sum.apply(o1));                                 //o1.sum 이랑 같은말임  o1의 함수인것처럼 apply를 쓰면 그렇게 실행시킬수있다
      alert(sum.apply(o2));

근데.. sum(o1);하면 왜안되는거고 왜 apply를 써야하는거지?
for문안에서 this를 사용했기때문에 배열의 처음부터 끝까지 순회를 하면서 그값을 더하는거여서
똑같지않나..?

```
