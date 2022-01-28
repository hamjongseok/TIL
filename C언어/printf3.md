# **🌈Printf🌈**

## **%d,%i구현**

---

- %d, %i 의 차이점
- printf 같은 output에서는 차이가 없고 scanf 같은 input 형식 지정자일 때 차이가 난다.

```c
int ft_print_di(va_list *ap)
{
    char *res;
    int nbr;
    int i;

    i = 0;
    nbr = va_arg(*ap, int); //int타입만큼 읽음
    res = ft_itoa(nbr); //숫자를 문자로 변환하는 itoa사용하여 res에저장
    while (res[i] != '\0')
    {
        write(1, &res[i], 1);
        i++;
    }
    free(res);
    return (i);
}
```

```c
int ft_intsize(int n)
{
    int i;

    if (n > 0) //양수라면 0
        i = 0;
    else //음수라면 '-' 를 넣어야 하기때문에 1부터시작
        i = 1;
    while (n != 0)
    {
        n /= 10;
        i++;
    }
    return (i);
}

char *ft_itoa(int n)
{
    int len;
    long long num; //언더플로우때문에
    char *result;

    num = n;
    len = ft_intsize(n); //할당해주는 만큼의 길이를 구하는 함수이용
    result = (char *)malloc(sizeof(char) * (len + 1));
    if (!result)
        return (NULL);
    result[len--] = '\0'; //마지막에 널 할당
    if (num < 0)
    {
        num *= -1;
        result[0] = '-';
    }
    if (n == 0)
        result[0] = '0';
    while (num > 0)
    {
        result[len--] = (num % 10) + '0'; //뒤에부터 나머지로 채움
        num /= 10;
    }
    return (result); // 문자열반환
}
```

- ## malloc시 free 문제로 애먹은점
- itoa함수에서 result에다가 말록을 했기때문에 거기에 free를 당연히 해줘야한다고 생각을했었디.
- 근데 그러자니 문자열을 반환할수가없고 굉장히 헷갈렸는데
- 공부를 해본결과 말록을 하게되면 우선 반환값은 할당된 메모리의 주소값이다.
  그렇기 때문에 시스템 메모리상에 할당된 공간이 있고 result는 그주소만 가지고있는것, 그걸 res에 넘기면 res를 free해주면 결국 그주소값을 free해주는것이다.
- free는 항상 다 사용한 뒤에 free해줘야 한다.

---

## %u 서식지정자 구현

- 부호없는 정수형으로 출력하라는 것
- %u 같은 경우에는 unsinged 자료 형이기 때문에 기존%d에서
  출력 한 부호의 출력을 제거한 로직을 사용하면 되었다.
- %u는 부호가없기때문에 최대 수가 int보다 2배는 더 크게나온다.
- 그렇기 때문에 unsigned int로 캐스팅하여 사용했다.
-

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/7b79684a-6f14-491f-89aa-cd8ff506d9a9/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-01-21_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_2.54.39.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220128%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220128T041154Z&X-Amz-Expires=86400&X-Amz-Signature=fdcf3199c0a1f7dacdd2d77316a263aee2ef3361d00c8a3a73fde37b48184174&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-01-21%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25202.54.39.png%22&x-id=GetObject)

- 출처 : 코딩도장

```c
int ft_print_u(va_list *ap)
{
    int i;
    unsigned int nbr;
    char *res;

    i = 0;
    nbr = va_arg(*ap, int);
    res = ft_itoa_u(nbr);
    while (res[i] != '\0')
    {
        write(1, &res[i], 1);
        i++;
    }
    free(res);
    return (i);
}
```

- itoa 함수는 unsigned int로 바꾼거 말고는 차이가 없고
- intsize에서 차이가 발생한다.

```c
int ft_intsize_u(unsigned int n)
{
    int i;

    i = 0;
    if (n == 0) //i = 0이라면 itoa함수에서 널 넣고 0도 넣어줘서 널이 들어가지않는다. 안해주면 쓰레기값 발생
        i = 1;
    while (n != 0)
    {
        n /= 10;
        i++;
    }
    return (i);
}
```

---

## %x

- %x는 소문자를 사용하여 숫자를 16진수로 출력
- %X는 대문자를 사용하여 숫자를 16진수로 출력하는것이다.
- 예전에 16진수를 변환하는것을 해본적이있는데 잘기억이 나지않아서 제일오래걸리고
  힘들었다..
- 처음에 생각한 로직은 나머지를 구해서 if문으로 하나씩 다처리하는방법이였는데
  그렇게 구현하면 숫자가 커짐에따라 제대로 된 변환이 불가능해져서 다시 첨부터 짰다..
- 그래서 내가 생각한 로직
- 1. 정수를 16진수로 바꿔서 문자열에 저장
- 2. 그러기 위해서는 malloc을 해야하고 len, 몇개가 필요한지, 길이를 구하는 len을 구하는 함수를 만들어야한다.

```c
int ft_print_x(va_list *ap)
{
    char *cp;
    unsigned int res;
    int i;

    i = 0;
    res = va_arg(*ap, unsigned int); //정수를 받음
    cp = ft_dectohex(res);           //문자열 cp에 정수를 16진수로 바꾼 문자열을 받는다.
    if (!cp)
        return (0);
    while (cp[i])
    {
        write(1, cp + i, 1);
        i++;
    }
    free(cp);
    return (i);
}
여기까지는 동일하다.
```

- ### 문자열 len값 구하는 함수

```c
int ft_hex_len(size_t res)
{
    int i;

    i = 1; //나머지 가 필요없다면 16보다 작다면 어차피 1이니간 , 그게아니라면 나머지를 구해줘야하니간 1
    while (res > 15)
    {
        res /= 16;
        i++;
    }
    return (i);
}
```

- ### 16진수 문자열로 바꾸는 함수

```c
char *ft_restohex(size_t res)
{
    char *cp;
    int len;
    int i;
    size_t pow; //%p 때문에 해줘야한다.
    char *hex_str;

    hex_str = "0123456789abcdef"; //16진수 문자열 할당
    i = 0;
    len = ft_hex_len(res); //문자의 len값을 구함
    cp = (char *)malloc(sizeof(char) * (len + 1));
    if (!cp)
        return (0);
    while (len > 0)
    {
        pow = ft_pow_hex(len - 1); //16의 0승 자리를 빼야하기때문에 -1
        cp[i] = hex_str[res / pow]; //몫을 처음에넣고
        res %= pow; // 나머지로 다시 나눠야하기때문에
        len--;
        i++;
    }
    cp[i] = '\0';
    return (cp);
}

size_t ft_pow_hex(int n) //%p때문에 해줘야한다.
{
    size_t ret;

    ret = 1;
    while (n--)
        ret *= 16;
    return (ret);
}

```

- (ex)
- 1234을 256으로 나눴을때 몫은 4 나머지는210이 나온다. 이말은
  256 \* 4 + 210 을 해줘야 1234가 나오게되고 210에서 16으로 풀어야 맞기때문이다.

---

- ### %X 구현
- 대문자만 바꿔주기때문에 upper함수를 이용해서 구현했다.

```c
char ft_toupper(char c)
{
    if (c >= 'a' && c <= 'z')
        c -= 32;
    return (c);
}

int ft_print_xx(va_list *ap)
{
    char *str;
    char c;
    unsigned int res;
    int i;

    i = 0;
    res = (unsigned int)va_arg(*ap, unsigned int);
    str = ft_restohex(res);
    if (!str)
        return (-1);
    while (str[i])
    {
        c = ft_toupper(str[i]);
        write(1, &c, 1);
        i++;
    }
    free(str);
    return (i);
}
```

---

## %p

- void \* 형식의 포인터 인자를 16진수로 출력한다.
- NULL포인터가 나온다면 0x0을 출력해 주어야 한다.

- 주소값을 어떻게 받아오는가? - C언어의 특징은 메모리 접근이다.
  메모리에 저장된 데이터는 타입을 지정해 주기 전까지는 그저 비트나열에 불과한다.
  반대로 생각하면 타입을 지정해 주는 순간 유의미한 데이터로 변한다.
- 예를들어

```c
 int *pi = (int *)malloc(sizeof(int) * 10);

va_list, malloc 같은 애들이 int , double, char 여러가지가 가능한이유는
해당 공간의 size를 정해주고, 적절하게 형변환이 일어나기 때문.

이건 va_list 에서 값을 뽑아올때도 같다.
그럼 va_arg 에서 int 를 지정해 준 것은
va_list에서 int만큼의 size를 가져가겠다 + 포인터 이동 라는 의도

그럼 주소값도 일단 주소값 형태로 받아오면 된다.
void *형 변수에 할당 후에 16진수 변환해서 출력해주면 된다.
컴파일러마다 운영체제마다 각종 환경마다 다르지만 나의 컴퓨터에서는 포인터 변수의 사이즈는 8바이트이다.

주소값의 가장 중요한 특성은
unsigned , 정답은 없다
unsigned 정수형중 void * 의 사이즈보다 큰 타입이면 된다.
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
- 비어있다면 (null)출력 예외처리
