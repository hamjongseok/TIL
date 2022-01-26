# **OPEN, READ**

## **OPEN 함수**

- 커널에 요청 할 수 있도록 지원되는 함수를 시스템콜 이라 한다.

```c
#include <fcntl.h>

int open(const char *pathname, int flags);
int open(const char *pathname, int flags, mode_t mode)

파일 오픈을 할 때 사용되는 시스템함수이다. open()함수는 리턴으로
int형 정수를 반환한다.
파일을 성공적으로 열었다면 파일지정번호를 이용
0보다 작은값이 반환될 경우는 파일열기에 실패한 경우
0 이상 = 정상적으로 파일을 열었으며, 열려진 파일의 file descriptor이다.
```

- pathname : 열기를 요청하는 파일. 상대경로 혹은 절대경로를 지정할 수 있다.
- flag : 어떤 방식으로 열것인지, bitwise 연산을 이용.
  - O_RDONLY = 읽기 전용
  - O_WRONLY = 쓰기 전용
  - O_RDWR = 읽기 , 쓰기 모두
  - O_CREAT = 파일없을 경우 파일 생성
  - O_EXCL = 파일 존재시 error 리턴
- mode : 파일 권한을 설정

```c
int open(const char *pathname, int flags);
int open(const char *pathname, int flags, mode_t mode)

왜 두개로 나뉘나 궁금해서 찾아본결과

일반적인경우
int open(const char *pathname, int flags);
파일을 새로 생성할경우
int open(const char *pathname, int flags, mode_t mode)

하지만 일반적인 경우에도 flags의 부가적인 옵션을 통해 파일을 생성할수있는걸로보인다.
```

---

## **read 함수**

- read 함수
- 헤더: unistd.h
- 형태: ssize_t read (int fd, void \*buf, size_t nbytes)
- 인수: int fd 파일 디스크립터void \*buf 파일을 읽어 들일 버퍼 size_t nbytes 퍼버의 크기
- 반환: size_t == -1 실패> 0 정상적으로 실행되었다면 읽어들인 바이트 수

```c
버퍼란?
버퍼(Buffer)의 사전적인 의미는 완충제 또는 완충제의 역할을 하는 것입니다.
컴퓨터 공학에서 불리는 버퍼 또한 장치와 장치 간의 데이터 전송을 할 때
완충작용을 하기 위한 임시 데이터 저장 공간입니다

버퍼에는 꼭 끝에 널로 초기화해줘야한다.
이것을 널 터미네이팅

1바이트 == 한개의 문자
```

read 함수는

bytes 수 만큼 fd를 읽어 buf에 저장한다.

- 리턴값 : 읽어 온 바이트 수. 실패 시 -1.
- 파일을 끝까지 읽었으면, 다음 번에는 더 이상 읽을 바이트가 없기 때문에 0을 반환한다.
