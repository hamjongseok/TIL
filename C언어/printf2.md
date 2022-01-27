# **🌈Printf🌈**

## **서식 지정자 구현**

---

- %c
  - 단일 문자 (character) 한 개를 출력합니다.
- %s
  - 문자열 (string) 을 출력합니다.
- %p
  - void \* 형식의 포인터 인자를 16진수로 출력합니다.
- %d
  - 10진수 숫자를 출력합니다.
- %i
  - 10진수 정수를 출력합니다.
- %u
  - 부호 없는 10진수 숫자를 출력합니다.
- %x
  - 소문자를 사용하여 숫자를 16진수로 출력합니다.
- %X
  - 대문자를 사용하여 숫자를 16진수로 출력합니다.
- %%
  - 퍼센트 기호 (%) 를 출력합니다.

---

## 가변인자 예시함수

- 서식 지정자를 구현하기 앞서 먼저 가변인자 함수를 이용해 공부를 해보았다.

```c
#include <stdio.h>
#include <stdarg.h>

int sum(int count, ...) //가변 인자 함수  . 1~ 10  10개의 인자
{
    int res;
    va_list ap; //가변 인수들을 저장해주는 저장공간 ap를 선언했다.
    int i;

		res = 0;
    va_start(ap, count); //ap를 초기화 (10으로 초기화),첫번째 가변인수를 가리킴

    for(i=0; i > count; i++) //0부터 10까지 돌린다.
        res += va_arg(ap, int); //읽으면서 다음 인자를 가리킴

    va_end(ap); //종료선언

    return res;
}

int main()
{
    printf("%d\n", sum(10, 1,2,3,4,5,6,7,8,9,10));

    return 0;
}
```

---

## ft_printf 기본함수

- 서식 지정자를 구현하기 앞서 가변인자 함수를 이용해 ft_printf기본 함수를 만들었다.

```c
int ft_printf(const char *fmt, ...) //fmt는 format으로 서식이라는뜻
{
    va_list ap; //va_list 가변인자 저장소
    int result; //문자의 개수 출력할 반환값 변수

    if (fmt == NULL) //예외처리 에러면 -1 음수반환
        return (-1);
    result = 0;
    va_start(ap, fmt); //va_start를 이용해 ap에게 가변인자의 첫주소를 알려줌
    while (*fmt != '\0') //fmt가 널일때까지
    {
        if (*fmt == '%') //fmt가 %라면
        {
            fmt++; //++을 해서 다음 문자를 확인하고
            if (*fmt == 0)
                break;
            result += ft_setform(fmt, &ap); //setform함수로넘어가고
        }                                  //result에다가 반환값저장
        else //그게아니라면 하나씩 다찍어낸다.
        {
            write(1, fmt, 1);
            result++; //출력하는 문자의 개수이므로 하나씩 ++
        }
        fmt++;
    }
    va_end(ap); //다끝나면 종료
    return (result);
}
```

- if 중간에 예외처리한이유

```c
 if (*fmt == 0)
            break;
 %가 끝이라면 마지막에 널을 검사하므로 문제가 생길수도있어 추가함

```

---

## ft_setform함수

```c
 if (*fmt == 0)
            break;
 %가 끝이라면 마지막에 널을 검사하므로 문제가 생길수도있어 추가함

```
