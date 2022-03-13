# **🍔`Today's Meal`🍔**

## **오늘의 식사 서비스 프로젝트** ⭐️⭐️

---

프로젝트 진행순서(미정)

```
ERD 클라우드(백 전반적 계획 수립) -> UI(부트스트랩 이용)프론트앤드 디자인(JSP(이클립스에서 하는거임)) -> 컨트롤러 MVC에서 C를 만든다
(여기에서 스프링, mysql등) -> 서버구축 아키텍처 구축(보안, ap설정, 도메인 설정 등)
-> aws배포(웹서버 설치, 자바설치, 깃설치) -> 끝
```

- ERD 클라우드
  - 무료 DB모델링 도구기능을 제공하는 사이트
  - 데이터베이스의 전반적인 구축계획을 가시적으로 볼수있게해준다.

---

# **필요 기초 지식관련 공부**

## `Web Server, Web Container, WAS`

### `Web server`

- 웹서버의 사전적 정의
  - 웹 브라우저 클라이언트로부터 HTTP요청을 받아 들이고 HTML 문서와 같은 웹페이지를 반환하는 컴퓨터 프로그램
  - HTTP란?
    - HTTP(Hypertext Transfer Protocol), 통신프로토콜이다.
    - 프로토콜이란 상호간에 정의한 규칙을 의미하며 특정 기기간에 데이터를 주고 받기위해 정의 되었다.
- 웹서버란 사용자가 요청하는 정적 콘텐츠를 전달하는 소프트웨어를 의미한다.
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ed9d0720-7776-4f13-b13d-4be64ca2c546/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-07_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.22.43.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220307T052317Z&X-Amz-Expires=86400&X-Amz-Signature=1966269decc4f8313a755ba690707a9ea7ddfc95e8d5322416bd7968ef8bf6c4&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-07%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25202.22.43.png%22&x-id=GetObject)
- 동적인 웹페이지도 응답을 하지만 동적인 웹페이지는 WAS에서 처리되며 웹서버 에서는 결국 정적인 컨텐츠를 제공한다.
- 하지만 웹서버는 정적 컨텐츠만 제공하는것은 아니고 웹서버가 동적 컨텐츠를 요청 받으면 WAS에게 해당 요청을 넘겨주고, WAS에서 처리한 결과를 클라이언트에게 전달해주는 역할도 한다.

정적 컨텐츠

- 정적컨텐츠 란 있는 그대로의 것을 제공하는 것을 의미한다.
  - 예) 서버에서 인간.jpg의 이미지를 보여주는 웹페이지가 있을때 인간 사진을 그대로 보여주는 것을 정적 컨텐츠라고 한다.

동적 컨텐츠

- 동적 컨텐츠란 서버가 컨텐츠를 처리하여 제공하는 것을 의미한다.
- 즉 사용자와 상호작용을 하며 때에 따라 다른 데이터를 보여주는 웹페이지를 의미함.

  - 예 ) 검색창에 ‘인간’을 검색하면 ‘인간’과 관련된 내용이 보여진다.

### `Web Container`

- Servlet, JSP를 실행할 수 있는 소프트웨어를 웹 컨테이너 또는 서블릿 컨테이너라고 한다.
- 웹 컨테이너의 역할
  - 웹서버에서 JSP를 요청하면 웹 컨테이너에서는 JSP파일을 서블릿 파일로 변환한 뒤 컴파일 하여 이것을 실행한 결과를 `웹서버에 전달한다.`
  - 쉽게 얘기해서 동적인 데이터를 처리해서 정적인 페이지로 생성해주는 소프트웨어 모듈
  - 서블릿들을 모아 관리
  - 새로운 요청이 들어올 때마다 새로운 스레드를 생성
  - 작업이 끝난 서블릿 스레드 자동 제거

```
스레드(thread)란?
스레드(thread)란 프로세스(process) 내에서 실제로 작업을 수행하는 주체를 의미한다.

모든 프로세스에는 한 개 이상의 스레드가 존재하여 작업을 수행한다.

또한, 두 개 이상의 스레드를 가지는 프로세스를 멀티스레드 프로세스(multi-threaded process)라고 한다.
```

### `WAS(Web Application Server)`

- Web Server와 Web Container가 합쳐진것
- Web Server는 정적 컨텐츠를 요청에 따라 전달 해주는 역할을 하는 반면에 WAS는 사용자의 요청에 따라 서버에서 프로그램을 실행 및 처리한 뒤 그것을 다시 정적인 페이지로 변환하여 반환하는 등의 동적인 처리를 담당
- 웹서버 단독으로는 처리할 수 없는 데이터 베이스의 조회나 다양한 로직 처리가 필요한 동적 컨텐츠를 제공한다.
- WAS는 JSP, Sevlet 구동 환경을 제공해주기 때문에 웹 컨테이너 혹은 서블릿 컨테이너라고도 부른다.
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2c0f2599-985c-458a-bdf2-e759a05c0789/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-07_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_8.25.46.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220307%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220307T112554Z&X-Amz-Expires=86400&X-Amz-Signature=481dffc2d8891bf502ed7baedcbb59672bec40356158a6f9dee8f565cca056e1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-07%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25208.25.46.png%22&x-id=GetObject)

### 여기서 든 의문점, WAS만 사용안하고 왜 웹서버와 같이 사용하는가?

- WAS는 DB조회 및 다양한 로직을 처리하는데 집중해야한다.
- 단순한 정적 컨텐츠는 웹서버가 맡고 기능을 분리시켜 서버 부하를 방지해야한다.
- 만약 WAS가 정적 컨텐츠요청까지 처리하면 부하가 커지고 동적 컨텐츠 처리가 지연되며 수행 속도가 느려지고 이로인해 페이지 노출 시간이 늘어나는 문제가 발생하여 효율성이 크게 떨어진다.

---

## Apache Tomcat

### 이번 프로젝트를 진행하면서 아파치 톰캣을 사용하는데 왜 사용하는지에 대해 공부를 해보았다.

- apach란 것은 소프트웨어 단체 이름 그리고 우리가 흔히 부르는 아파치서버라는 것은 이제단에서 후원하는 오픈소스 프로젝트 커뮤니티에서 만든 http웹서버를 지칭하는 말이다.
- 즉 ,아파치 http서버는 http요청을 처리하는 웹서버인 것이다
- 우리가 사용하는 아파치 톰캣은 아파치 소프트웨어 재단에서 개발한 서블릿 컨테이너만 있는 웹 애플리케이션 서버이다.
- 톰캣은 웹 서버와 연동하여 실행할 수 있는 자바 환경을 제공하여 자바서버 페이지와 자바 서블릿이 실행할 수 있는 환경을 제공하고 있다.
- 위에서 공부한 WAS의 종류이고 Tomcat WAS라고도 불린다.

### 그런데 왜 Apache Tomcat인가?

- 기본적으로 아파치와 톰캣의 기능은 나뉘어져 있지만, 톰캣 안에 있는 컨테이너를 통해 일부 아파치의 기능을 발휘하기 때문에 보통 아파치 톰캣으로 합쳐서 부른다고 한다.
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/30ba04bc-f943-443a-988c-a5473c224127/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-09_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.11.22.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220308%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220308T153831Z&X-Amz-Expires=86400&X-Amz-Signature=212b86dd4686b929bca70f78aa7d703557cd0df4ecb165fc8d8860cc38d1e4de&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-09%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB%252012.11.22.png%22&x-id=GetObject)

---

## `JSP와 서블릿`

### `JSP`

- JSP 란 JavaServer Pages 의 약자이며 HTML 코드에 JAVA 코드를 넣어 동적웹페이지를 생성하는 웹어플리케이션 도구이다.
- JSP 가 실행되면 자바 서블릿(Servlet)으로 변환되며 웹 어플리케이션 서버(WAS)에서 동작되면서 필요한 기능을 수행하고그렇게 생성된 데이터를 웹페이지와 함께 클라이언트로 응답한다.
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0212c06f-fbc0-4504-b4fe-6de4d9f94155/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-12_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.37.11.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220312%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220312T053724Z&X-Amz-Expires=86400&X-Amz-Signature=9969c6a99dd44e1746b332fe9ca8c83b29bef48ee25220a526df25fe9283f597&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-12%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25202.37.11.png%22&x-id=GetObject)

```
1. 클라이언트가 어떤 동작을 함으로써 hello.jsp 를 요청하였다.

2. JSP 컨테이너가 JSP 파일을 읽는다.

3. JSP 컨테이너가 Generete (변환) 작업을 통해 Servlet ( .java )  파일을 생성한다.

4. .java 파일은 다시 .class 파일로 컴파일된다.

5. Execute (실행) 을통해 HTML 파일을 생성하여 JSP 컨테이너 에게 전달한다.

6. JSP 는 HTTP 프로토콜을 통해 HTML 페이지를 클라이언트 에게 전달한다.
```

### `자바 서블릿(Java Servlet)`

- 서블릿이란 웹페이지를 동적으로 생성하기 위해 서버측 프로그램을 말한다.
- 이는 자바 언어를 기반으로 만들지며 웹 어플리케이션 서버 ( Web Application Sever ) 위에서 컴파일 되고 동작한다.
- 간단히 말해서 서블릿이란 자바를 사용하여 웹을 만들기 위해 필요한 기술이다. 좀더 들어가서 설명하면 클라이언트가 어떠한 요청을 하면 그에 대한 결과를 다시 전송해주어야 하는데, 이러한 역할을 하는 자바 프로그램이다.
- 예시
  - 어떠한 사용자가 로그인을 하려고 할 때. 사용자는 아이디와 비밀번호를 입력하고, 로그인 버튼을 누른다. 그때 서버는 클라이언트의 아이디와 비밀번호를 확인하고, 다음 페이지를 띄워주어야 하는데, 이러한 역할을 수행하는 것이 바로 서블릿(Servlet)

### 서블릿의 특징

- 클라이언트의 요청에 대해 동적으로 작동하는 웹 어플리케이션 컴포넌트
- html을 사용하여 요청에 응답한다.
- Java Thread를 이용하여 동작한다.
- MVC 패턴에서 Controller로 이용된다.
- HTTP 프로토콜 서비스를 지원하는 javax.servlet.http.HttpServlet 클래스를 상속받는다.
- UDP보다 처리 속도가 느리다.
- HTML 변경 시 Servlet을 재컴파일해야 하는 단점이 있다.

### 서블릿의 동작 방식

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/57085489-2a51-4563-9811-e92f7fc50459/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-13_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.43.48.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220313%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220313T034434Z&X-Amz-Expires=86400&X-Amz-Signature=7cff56012966f79d7080de020553e622ee3c343710f7723fa943b301510530b8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-13%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252012.43.48.png%22&x-id=GetObject)

```
1. 사용자(클라이언트)가 URL을 입력하면 HTTP Request가 Servlet Container로 전송

2. 요청을 전송받은 Servlet Container는 HttpServletRequest, HttpServletResponse 객체를 생성

3. web.xml을 기반으로 사용자가 요청한 URL이 어느 서블릿에 대한 요청인지 찾는다.

4. 해당 서블릿에서 service메소드를 호출한 후 클리아언트의 GET, POST여부에 따라 doGet() 또는 doPost()를 호출

5. doGet() or doPost() 메소드는 동적 페이지를 생성한 후 HttpServletResponse객체에 응답을 보낸다.

6. 응답이 끝나면 HttpServletRequest, HttpServletResponse 두 객체를 소멸
```

### GET , POST

- GET, POST는 클라이언트가 서버로 요청을 보내는 방법인 HTTP Method의 2가지 방식이다. 간단하게만 알아보기
- GET
  - 영어 Get이라는 단어는 가져오다라는 뜻 그대로, 우리가 필요한 정보를 얻기 위해 도서관에서 책을 빌려 가져오는(GET)상황과 유사하게 GET은 어떠한 정보를 가져와서 조회하기 위해서 사용되는 방식이다.
- POST
  - POST라는 단어는 부치다, 제출하다라는 뜻을 가지고 있다. 예를 들어 우리가 어디에 서류를 제출하는 것은 우리에 대한 정보를 제출하여(POST) 추가하기 위한것 이러한 상황과 유사하게 POST 방식은 데이터를 서버로 제출하여 추가 또는 수정하기 위해서 사용하는 방식이다.

### JSP 와 서블릿의 차이점

- JSP 와 서블릿의 차이점은 결과적으로 하는일은 동일하지만 JSP 는 HTML 내부에 JAVA 소스코드가 들어감으로 인해 HTML 코드를 작성하기 간편하다는 장점이있다
- 서블릿은 자바코드내에 HTML 코드가 있어서 읽고 쓰기가 굉장히 불편하기 때문에 작업의 효율성이 떨어진다.

### 같이 쓰는이유

- JSP 로 작성된 프로그램은 서버로 요청시 서블릿(Servlet) 파일로 변환되어 JSP 태그를  분해하고 추출하여 다시 순수한 HTML 를 변환한다.
