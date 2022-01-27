# **GNL**

## **정적변수의 특징**

---

- 정적 변수는 전역 변수처럼 프로그램이 종료되지 않는 한 메모리가 소멸되지 않고, 특별히 초깃값을 지정하지 않아도 **자동으로 0**을 가진다.
- 주의 사항이 있다면 정적 변수도 전역 변수와 마찬가지로 초기화할 때 반드시 상수를 초기화해야한다.
- 정적 변수는 프로그램 시작 시 메모리에 할당되고, 프로그램 종료 시 메모리가 해제된다.(변수의 범위를 벗어나도 값을 유지한다.)
- 자료형 앞에 `static` 키워드를 붙임
- 정적 변수는 프로그램 시작 시 메모리에 할당되고, 프로그램 종료 시 메모리가 해제된다.(변수의 범위를 벗어나도 값을 유지한다.)
- 함수의 매개변수로 사용할 수 없다 함수의 매개변수에 static을 붙이더라도, 매개 변수는 정적 변수가 되지 않으며 값이 유지되지 않음. (잘못된 문법)

## GNL 과제

- 과제를 이해하는데 너무 오랜시간이 걸렸다..
- gnl은 주어진 fd에 해당하는 파일을 라인단위로 글을 읽어온다.
- 파일을 open 함수로 열게되고 그 파일에 대한 fd값으로 read함수로 읽는다
- 그 라인에 개행이있다면 개행까지 출력하고 그뒤에는 저장을 해서
- 다음 read함수로 라인을 읽을때 저장한 문장뒤에 갖다붙혀서 출력하는 형태
- 그렇기 때문에 정적 변수 `static`을 사용해야한다.

```c
예를들어 fd에 해당하는 파일이 12345\n이고 버퍼사이즈가 3이라면
read를 실행시키면 버퍼에 123이 저장된다.
read를 한번더 실행시키면 읽어온 부분은 넘어가고
45부터 알아서 읽어온다.
반환값이 -1일때에는 에러처리를 해줘야 한다.(read의 반환값)
```

```c
char    *get_next_line(int fd)
{
    static char     *backup[OPEN_MAX];//이전의 문자를 저장하기위해
    char            *buf;//버퍼 리드함수

    if (fd < 0 || BUFFER_SIZE < 1)
        return (0);
    buf = (char *)malloc(sizeof(char) * (BUFFER_SIZE + 1));
    //BUFFER_SIZE만큼만 들어가기때문에
    if (buf == 0)
    {
        free(backup[fd]);
        return (0);
        //buf가 할당에 실패했다면 사용하지않는 backup[fd]를 free해주고
        //프로그램 종료
    }
    if (!ft_get_backup(backup, fd, buf))
        return (0);
    free(buf); //사용한 buf를 free
    return (ft_make_backup(backup, fd));
}
```

- malloc을 사용하기 때문에 불필요한 경우가되면 free를 항상해줘야한다.
- static char \*backup에서 OPEN_MAX를 쓰는이유는 ?
  - openmax는 오픈함수로 열수있는 최대 개수 , 한 프로세서 최대로 받을수있는값

---

## ft_get_backup

- 파일을 read함수로 읽고 buf를 저장, backup에 붙여주는 과정
- 매개변수
  - 저장할 static backup, fd값, read함수에 사용될 buf

```c
int ft_get_backup(char **backup, int fd, char *buf)
{
    int len;

    len = 1;
    while (len != 0 && !ft_strchr(backup[fd], '\n'))
    {
        len = read(fd, buf, BUFFER_SIZE);
        if (len == -1) //에러라면 다 free해줘야한다.
        {
            free(buf);
            free(backup[fd]);
            return (0);
        }
        buf[len] = '\0'; //마지막에 널터미네이팅
        backup[fd] = ft_strjoin(backup[fd], buf);
    }
    return (1);
}
```

- len 을 1로 할당하고 while 조건문에 len != 0인이유
  - while안에서 len = read();를 사용하는데
  - read함수에서 파일의 끝, eof를 만나면 0을 반환하고 에러는 -1
  - -1은 밑에서 예외처리를 해주었다. 즉 파일의 끝까지 계속 돌리게한것
- buf[len] = '\0';
  - 처음에 buf의 끝에 널터미네이팅을 해주지않아서 엄청 애 먹었다..
  - 계속 다른 엉망인 문자 값들이 나와서 왜그런지 계속 생각했다..

```c
문자열을 다룰때 맨마지막에 널을 넣어야 하는 이유

1. 널문자를 넣어야 문자의 끝이 어딘지 알수있다.
2. ft_strlen 등 문자열을 다루는 함수들은 널문자를 기준으로 그 전까지 오는 문자들만을 하나의 문자열로 다루기 때문
3. 또한 널문자가 제대로 들어가있지 않은 경우 (null-terminate되어있지 않은 경우)
이러한 메모리 관련 함수들을 사용할 때 문자열의 끝이 어딘지 명확하지 않아 다른 메모리 영역을 침범할 가능성이 매우 높아진다.
```

- !strchr(backup[fd], '\n')
  - strchr 함수를 이용하여 개행을 찾게되면 나오는 조건을 달았다.
  - 개행을 기준으로 짤라야 하기때문에

```c
int ft_strchr(const char *s, int c)
{
    if (s == 0)
        return (0);
    while (*s)
    {
        if (*s == (char) c)
        return (1);
        s++;
    }
    return (0);
}
```

- 0과 1을 이용하여 while문에서 사용될것이기 때문에 int형으로 했다.
- 개행을 찾으면 1리턴
