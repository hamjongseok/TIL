# **🍔`Today's Meal`🍔**

## `JSTL` ⭐️

- jstl(JSP Standard Tag Library)
- JSP에서 java코드가 들어갈때마다 매번 <% ~~ %> 이 태그를 넣어 사용하면 가독성도 굉장히 떨어지고 사용하기가 불편해진다 그래서 나온것이 JSTL라이브러리이다.
- JSP는 자신만의 태그를 추가할 수 있는 기능을 제공하고 있다.
- <jsp:include>나 <jsp:usebean>과 같은 커스텀 태그처럼 연산이나 조건문이나 반복문인 if문, for문, DB를 편하게 처리할 수 있는것이 JSTL이다.

```
아직 jstl 관련 태그 공부하는것은 순서가 아닌것 같아서 넘어감
```

---

## `EL` ⭐️

- Expression Language의 약자로써 내장 객체의 데이터를 JAVA를 이용하지 않고 출력하는 것
- 주로 JSTL과 함께 사용되며 '$', '{}'응 이용하여 값을 표현

```
EL도 마찬가지로 자바먼저 하고 공부
```

---

## `MVC 패턴` ⭐️⭐️⭐️

- MVC 는 Model, View, Controller의 약자이다.
- 하나의 애플리케이션, 프로젝트를 구성할 때 그 구성요소를 세가지의 역할로 구분한 패턴
- 즉 개발 할 때, 3가지 형태로 역할을 나누어 개발하는 방법론이다.
- 비지니스 처리 로직과 사용자 인터페이스 요소들을 분리시켜 서로 영향없이 개발 하기 수월하다는 장점이 있다.

`Model`은 어플리케이션이 “무엇”을 할 것인지를 정의한다. 내부 비지니스 로직을 처리하기 위한 역할

- 처리되는 알고리즘, DB 와 상호작용(**CRUD** Create Read Update Delete), 데이터 등등..

`Controller`는 모델이 “어떻게” 처리할 지를 알려주는 역할을 할 것이고, 모바일에서는 **화면의 로직처리** 부분이다. 화면에서 사용자의 요청을 받아서 처리되는 부분을 구현되게 되며, 요청 내용을 분석해서 Model과 View에 업데이트 요청을 하게 된다.

- **사용자**로 부터의 입력 을 받고 Model 또는 View중개인 역할

`View`는 화면에 “무엇” 인가를 **보여주기 위한 역할**을 한다. 컨트롤러 하위에 종속되어, 모델이나 컨트롤러가 보여주려고 하는 모든 필요한 것들을 보여줄 것이다.

- **최종 사용자**에게 “무엇”을 화면(UI)으로 보여줌

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f0b0c7a8-6bbd-4a4b-b8e6-6569f646affb/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-13_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.34.30.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220313%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220313T062800Z&X-Amz-Expires=86400&X-Amz-Signature=d193d06a085d51485b6c181411022f42122ebaa035514f14059b3e190a0573e2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-13%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25202.34.30.png%22&x-id=GetObject)
쉽게 말해서 다시 정리하자면

Model : 데이터와 관련된 부분

View : 사용자에게 보여지는 부분

Controller : Model과 View를 이어주는 부분

## MVC패턴을 지키는 규칙

1. Model은 Controller와 View에 의존하지 않아야한다
   - 즉 Model 내부에 Controller와 View에 관련된 코드가 있으면 안된다.
   - 언제든 깔끔하고 정제된 데이터를 꺼내 쓸 수 있게 뷰나 컨트롤러의 코드를 섞어넣지않고 데이터와 관련된 코드만 존재
2. View는 Model에만 의존해야 하고, Controller에는 의존하면 안된다.
   - View 내부에 Model의 코드만 있을 수 있고, Controller의 코드는 있으면 안된다.
3. View가 Model로부터 데이터를 받을 때는, 사용자마다 다르게 보여주어야 하는 데이터에 대해서만 받아야 한다.
   - 기본적으로 구성되어있는 모든 사용자가 확인할수있는 UI == View
   - 사용자마다 다른 정보 == Model
4. Controller는 Model과 View에 의존해도 된다.
   - Controller는 Model과 View의 코드가 있을 수 있다.
   - 그 이유는 Controller는 모델과 뷰의 중개자 역할을 하면서 전체 로직을 구성하기 때문
5. View가 Model로부터 데이터를 받을때, 반드시 Controller에서 받아야 한다.
