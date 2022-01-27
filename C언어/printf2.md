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

---

## ft_setform함수, %c

- if문을 통해 서식지정자마다 정해진 함수로 들어가는 함수

```c
 int ft_setform(const char *fmt, va_list *ap)
{
    char c;

    c = 0;
    if (*fmt == '%') //%라면 바로 %찍고 리턴
        return (write(1, "%", 1));
    if (*fmt == 'c') //c 라면
    {
        c = va_arg(*ap, int); //ap를 int타입으로 읽는다.
        write(1, &c, 1); //c  바로찍어냄
        return (1);
    }
    else if (*fmt == 's')
        return (ft_print_s(ap));
    else if (*fmt == 'd' || *fmt == 'i')
        return (ft_print_di(ap));
    else if (*fmt == 'u')
        return (ft_print_u(ap));
    else if (*fmt == 'x')
        return (ft_print_x(ap));
    else if (*fmt == 'X')
        return (ft_print_xx(ap));
    else if (*fmt == 'p')
        return (ft_print_p(ap));
    return (0); //위에 해당이안되면 0리턴
}

```

- 출력 값이 `'\0'`이 넘어와도 출력을 하고 카운트를 해야합니다.
- 출력은 안되지만 카운트는 1이 되어야한다.

### char 자료형과 int 자료형

```
int num = va_arg(ap, int);
char ch = va_arg(ap, int);
```

- %d, %c같이 int나 char형의 값을 읽어올 때 동일하게 int형을 사용했다.
- int형은 4byte char형은 1byte인데 왜 똑같이 사용하는 걸까?
  - va_list 자료형이 내부적으로 가르키는 값은 4byte씩 나뉘어져 있어서 char, int 자료형을 동일하게 사용한다.
  - va_list 자료형은 포인터 변수이고, 포인터 변수는 4byte이기 때문에 가변 인자들이 4byte씩 나뉘어져있다고 생각한다.

---

## %s 구현

```c
 int ft_print_s(va_list *ap)
{
    int c;
    char *str;

    c = 0;
    str = (char *)va_arg(*ap, char *); //char * 크기만큼 값을 가져오고 그 크기만큼 이동, str에 넣음
    if (!str) //str이 비어있다면 예외처리 (null)출력해야한다.
        return (write(1, "(null)", 6));
    while (*str) //str 끝까지
    {
        write(1, str, 1);
        str++;
        c++; //출력개수
    }
    return (c);
}
```

- ap => 주소값을 이용해서 사용하는것이기때문에 포인터인채로 넘겨야한다.
- 널 포인터라면 (null)출력 예외처리
