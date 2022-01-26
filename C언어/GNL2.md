# **GNL**

## **ft_get_backup**

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

- read함수로 파일을 읽고 반환값을 Len에 저장
- read함수로 buf에 문자열 저장
- buf의 마지막에 널터미네이팅
- bacup[fd]에 ft_strjoin을 이용해서 buf의 문자열을 저장시켜준다.

## ft_strjoin

```c
static char *ft_strjoin(char *s1, char *s2)
{
    size_t  i;
    size_t  j;
    char    *str;

    if (!s1)
    {
        s1 = (char *)malloc(sizeof(char) * 1);
        s1[0] = '\0';
    }
    if (!s1 || !s2)
        return (0);
    str = (char *) malloc(sizeof(char) * (ft_strlen(s1) + ft_strlen(s2) + 1));
    if (str == 0)
        return (0);
    i = -1;
    j = 0;
    if (s1)
        while (s1[++i] != '\0')
            str[i] = s1[i];
    while (s2[j] != '\0')
        str[i++] = s2[j++];
    str[ft_strlen(s1) + ft_strlen(s2)] = '\0';
    free(s1); //다 사용했기에 free를 꼭해줘야한다. 아니면 leak 발생
    s1 = NULL; //댕글링 포인터
    return (str);
}
```

- ft_strjoin은 문자열을 붙여주는 함수이다.
- s1과 s2의 길이를 구하고 그의 합 + 1 (널) 로 말록으로 할당
- static 함수를 사용하는 이유
  - 함수의 이름이 중복될 경우를 대비해서, 이함수는 이파일내에서만 사용하는 함수이라는 뜻이다.

```c
   if (!s1)
    {
        s1 = (char *)malloc(sizeof(char) * 1);
        s1[0] = '\0';
    }
```

- 이렇게 해주는 이유 ?
  - 처음에 들어왔을때 s1 즉 backup에 이렇게 할당 해주지않는다면 세그폴트가 발생한다.
  - 이 방법 말고 처음 gnl함수에서 빈문자열 strdup로 사용해도된다.
  - strlen 등등 문제 발생요인

---

## ft_make_backup

- backup을 만들어주는 함수
- substr 문자열 자르는 함수를 사용하여 개행까지는 line에다가 담고 리턴
- 개행 뒤부터는 new_backup에 저장한뒤 backup[fd]에 저장

```c
int ft_find_char(char *str)
{
    int i;

    i = 0;
    while (str[i] != '\0')
    {
        if (str[i] == '\n')
        break ;
        i++;
    }
    return (i);
}

static char *ft_make_backup(char **backup, int fd)
{
    char    *line;
    char    *new_backup;
    int     i;

    if (*backup[fd] == 0) //예외처리
    {
        free(backup[fd]);
        backup[fd] = 0;
        return (0);
    }
    i = ft_find_char(backup[fd]); //개행의 인덱스를 i에다가 저장
    line = ft_substr(backup[fd], 0, i + 1); //인덱스 는 0부터 시작하므로 + 1해줘야 맞는다.
    if (line == 0)
        return (0);
    new_backup = ft_substr(backup[fd], i + 1, ft_strlen(backup[fd]) - (i + 1));
    if (new_backup == 0)
    {
        free(line);
        return (0);
    }
    free(backup[fd]);
    backup[fd] = new_backup;
    return (line);
}

```

- i = ft_find_char 함수를 이용하여 개행의 인덱스값을 저장
- ft_substr을 이용하여 line에다가 개행까지 저장을 한다.

```c
char    *ft_substr(char const *s, unsigned int start, size_t len)
{
    char    *tmp;
    size_t  s_len;
    size_t  i;

    i = 0;
    s_len = ft_strlen(s);
    if (s_len < start)
        return (ft_strdup(""));
    if (len > ft_strlen(s + start)) //할당할때 필요없는 부분을 버린다. &s[start]의 의미
        len = ft_strlen(s + start);
    tmp = (char *)malloc(sizeof(char) * (len + 1));
    if (!tmp)
        return (NULL);
    ft_strlcpy(tmp, s + start, len + 1);
    return (tmp);
}
```

- 1. 부분 문자열 (substring) 을 생성할 원본 문자열
- 2. 부분 문자열의 맨 처음 인덱스
- 3. 부분 문자열의 최대 길이

```c
new_backup = ft_substr(backup[fd], i + 1, ft_strlen(backup[fd]) - (i + 1));
```

- new_backup에다가 개행 그다음 부터 끝까지 잘라서 붙여준다.
- 필요없는 backup[fd] 는 free해주고 다시
- backup[fd]에다가 new_backup을 넣어준다.
- 이런식으로 개행을 기준으로 개행까지 자르고 리턴, 개행 다음부터 문자열을 정적변수로 저장뒤 붙여서 eof를 만날때까지 리턴 해주면 끝!

- GNL을 통해 느낀점
  - 어떠한 함수인지 이해가 처음에 가지않아서 이해하는데 굉장히 오래걸렸다.
  - 그래도 한번 이해하니간 어느정도 생각대로 풀수있었고 정적변수를 활용해서 풀었기 때문에 정적변수의 개념에대해서 완전히 잡힌것같다
  - malloc을 하고 leak발생하는점에서 메모리누수에 대해 깊게 생각하고 해결할 수 있어 좋았던것같다.
