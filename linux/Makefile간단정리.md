# **Makefile**

## **Makefile의 정의**

- linux상에서 반복 적으로 발생하는 컴파일을 쉽게하기위해서 사용하는 make 프로그램의 설정 파일이다.

- Makefile을 통하여 library 및 컴파일 환경을 관리 할수 있다.

## C 프로그램의 빌드 절차

1. 컴파일 : 소스파일을 각각 컴파일하여 Object파일(\*.o)을 생성하고,
2. 링크 : 이들을 한 데 묶는 링크 과정을 통해서 실행 파일인 a.out을 생성한다.여기서 소스파일에 정의된 함수를 main에서 호출하는 **의존성**이 존재한다.

#

#### Compile이란?

내가 소스 코드(.c)를 작성하고 실행 파일 (.exe)을 만드는 것을 컴파일이라고 생각하겠지만 이것은 `컴파일러`가 하는 역할이지 컴파일은 아니다.
`컴파일`의 개념은 소스 코드(원시 코드) 목적 파일로 바꾸는 것이다.

<!-- Image -->

![image description](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/77677ee2-8390-42f5-881b-88ad36191485/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-11-17_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_4.14.40.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220121%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220121T023515Z&X-Amz-Expires=86400&X-Amz-Signature=1eb7b649e18bd49d925f809a0e58722ab33b1e15e3bc2c3cdc632ca2b1f6a271&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202021-11-17%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25204.14.40.png%22&x-id=GetObject)

#

## Makefile을 사용하는 이유

- 각 파일에 대한 반복적 명령의 자동화로 인한 시간 절약
- 프로그램의 종속 구조를 빠르게 파악할수 있으며 관리가 용이
- 단순 반복 작업 및 재작성을 최소화

## Makefile 기본 패턴

```
CC=<컴파일러>
CFLAGS=<컴파일 옵션>
LDFLAGS=<링크 옵션>
LDLIBS=<링크 라이브러리 목록>
OBJS=<Object 파일 목록>
TARGET=<빌드 대상 이름>

all: $(TARGET)

clean:
    rm -f *.o
    rm -f $(TARGET)

$(TARGET): $(OBJS)$(CC) -o $@ $(OBJS)
```

Makefile은 기본적으로 목표(target), 의존 관계(dependency), 명령(command)의 세개로 이루어진 기분적인 규칙(rule)들이 계속적으로 나열되어 있다고 봐도 무방하다.

#

ar - 정적 라이브러리는 컴파일된 오브젝트 파일들이 하나의 아카이브로 묶여있는
상태로, 오브젝트 파일들을 묶어주는 명령어.
r : 새로운 오브젝트 파일이면 추가, 기존 파일이면 치환.
c : 아카이브(라이브러리 파일) 생성, 존재하지 않는 아카이브를 작성하는
경우에도 경고 메세지를 출력하지 않음.

$@ : target
$< : 열거된 depend 중 가장 왼쪽의 depend 파일
$^ : depend 전체 파일
$? : target과 depend의 변경 날짜를 비교해 변경된 depend만 선택하는 매크로이다.
