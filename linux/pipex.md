# **❌ PipeX ❌**

## **기본 개념**

---

```c
./pipex file1 cmd1 cmd2 file2

실행결과가

< file1 cmd1 | cmd2 > file2

같은 결과가 나와야한다.

file1및 file2는 파일 이름이고 cmd1 및 cmd2는 매개변수에 대응하는 Shell 명령어이다.
```

- file1을 읽어서 cmd1 을 실행하고 그 결과를 cmd2의 입력으로 준다.
  cmd2를 실행한 결과를 file2에 출력한다.

---

## **개념 공부**

### char \*envp[]

- <시스템 환경변수>
- 메인함수의 세번째인자로 이 시스템 환경변수에 대한 정보를 받아올수 있다.
- 프로세스가 실행이 되면 시스템으로부터 환경 변수 정보를 받아서 이정보를 바탕으로 실행이된다.
- 환경변수 문자열 전체를 받으며 환경변수는 OS가 실행되는 환경에 대해 정의된 값들이다. 그리고 환경변수 문자열의 마지막에는 NULL문자열이 들어있고 이것을 활용하여 인자뿐만 아니라 현재 프로그램을 위한 새로운 환경변수를 정할 수 있다.
  - envp 환경변수를 왜 사용하는건지 아직 모르겠군..

### redirection

- '<' : 입력 redirection

  - 정확히는 "[n] < word" 의 꼴로 사용한다.
  - n 은 redirect할 파일 디스크립터가 되고 word에는 읽을 파일 이름이 된다.
  - n을 명시하지 않으면 기본 0 이 들어간다.

- '>' : 출력 redirection
  - [n]>[|]word 의 꼴로 사용한다.
  - n 파일 디스크립터로 write을 목적으로 word 파일을 오픈 후 결과를 출력.

---

## 사용 함수

### access

```c
#include <unistd.h>

int access(const char *path, int mode);
```

파일의 권한을 체크하는 함수

path : 파일 명

mode : mask 값(비트연산을 이용해서 여러 개 확인 가능)

- R_OK : 파일 존재 여부, 읽기 권한 여부
- W_OK : 파일 존재 여부, 쓰기 권한 여부
- X_OK : 파일 존재 여부, 실행/검색 권한 여부
- F_OK : 파일 존재 여부
- 성공시 0, 실패 시 -1 반환, errno설정된다 (실패시)

### OPEN

```c
int open(const char *filename, int flag, [mode_t mode]);
```

파일을 여는 함수

filename : 파일명

flag

- O_RDONLY : 파일을 읽기 전용으로 연다. (Read Only)
- O_RDWR : 파일을 쓰기와 읽기용으로 연다. (Read & Write)
- O_CREAT : 파일이 없으면 생성한다. 이 플래그를 명시하면, open 함수에 - - Permission 정보를 추가로 더 받아야 한다. 파일이 존재하면 연다.
- O_TRUNC : 파일이 이미 존재하고 write-only, read-write모드로 열 수 있는 경우, 파일 사이즈를 0으로 초기화시킨다
- mode : O_CREAT 옵션 사용에 의해 파일이 생성될 때 지정되는 파일 접근 권한

- 읽기 권한 : 4
- 쓰기 권한 : 2
- 실행 권한 : 1
  - 420 을 하려면 8진수 0644를 입력해야 한다

## perror : 시스템 에러 메시지 출력 함수

```c
#include <stdio.h>

void
perror(const char *s);

```

**매개변수**

- `*s` : 추가적으로 전달하고자 하는 사용자 정의 메시지

---

# Mlx 함수

## Mlx 초기화하기

```c
#include <mlx.h>

int main(void)
{
	void *mlx_ptr;

	mlx_ptr = mlx_init();
	return (0);
}

mlx_ptr은 mlx_init()함수가 리턴하는 주소를 가리키게 된다.

mlx_init()함수는 디스플레이와 우리의 프로그램을 연결시켜주는 초기화 함수이다.
```

## window창 생성하기

```c
win_ptr = mlx_new_window(mlx_ptr, 500, 500, "Hellow World!");

mlx_ptr : mlx_init이 반환한 연결 식별자
size_x : 창의 가로 사이즈
size_y : 창의 세로 사이즈
title : 타이틀 바에 표시될 문자열

```

- 초기화 하지 않은 mlx_ptr이 mlx_new_window함수로 전달된다면 segfault를 발생한다.
- 함수는 창을 생성하는 것 까지만 작동하고 실제로 모니터상에 창을 띄우진 않는다. mlx_loop 함수가 실제로 모니터상에 창을 띄우는 역할을 해준다.

```
int mlx_loop(void *mlx_ptr)

mlx_ptr :  디스플레이에 연결되어 있는 mlx_ptr
return value : no return
```

- 마지막에 이걸 쳐줘야 프로그램이 종료하지 않고 계속 돌아간다.

## 키 Hook

```
int mlx_hook(void *win_ptr, int x_event, int x_mask, int (*func)(), void *param)

윈도우 식별자
X11 event
x_mask(mac에선 미사용으로 0 입력)
호출할 함수 포인터(눌린 키와 창에서 눌린 좌표 등이 전달됨)
함수에 전달할 파라미터를 인자로 받는 함수

```

MAC OS의 키보드 코드이다.

```c
#define X_EVENT_KEY_PRESS 2 // mlx_hook 함수의 두번째 인자
#define X_EVENT_KEY_RELEASE 3 // x_event에 들어가는 값 , 이게 왜있어야 하는지 모르겠다.

#define KEY_W 13
#define KEY_A 0
#define KEY_S 1
#define KEY_D 2
#define KEY_ESC 53 // MAC OS의 키보드 코드 들이다.


typedef struct  s_param // 키 값은 입력받고 정해진 동작을 수행했는지 여부를 판단하기 위해 선언
{
    int x; //x값
    int y; //y값
}   t_param;

void param_init(t_param *param) // 구조체 param 초기화 함수
{
    param->x = 0;
    param->y = 0;
}

int key_press(int keycode, t_param *param) //어떤키 눌렸는지 판단하고, 정의된 행동을 수행하는 함수
{
    if (keycode == KEY_W) // W 키를 누르면 param.x값이 1 증가입니다.
        param->x++;
    else if (keycode == KEY_S) // S 키를 누르면 param.x값이 1 감소입니다.
        param->x--;
    else if (keycode == KEY_A) // A 키를 누르면 param.y 값이 1 증가한다.
        param->y++;
    else if (keycode == KEY_D) // D 키를 누르면 param.y값이 1 감소한다.
        param->y--;
    else if (keycode == KEY_ESC) //ESC키를 누르면 프로그램 종료
        exit(0);
    printf("(x,y): (%d, %d)\n", param->x, param->y); //param의 값 확인
    return (0);

```

```c

#define X_EVENT_KEY_PRESS 2 // mlx_hook 함수의 두번째 인자
#define X_EVENT_KEY_RELEASE 3

x_event에 X11 events라고 mlx에 등록된 이벤트의 번호다. 번호에 대응되는 이벤트를 후킹한다.

x11 events:
02: KeyPress
03: KeyRelease
```

---

## MAKEFILE

---

## 이미지

- xpm확장자로 변환후 mlx함수를 이용해서 맵에 띄운다.
- mlx_xpm_file_to_image와 mlx_put_image_to_window 을 활용

```c

  img = mlx_xpm_file_to_image(mlx_ptr, "./images/wall.xpm", &img_width, &img_height);

  mlx포인터, 파일 주소, 가로 세로 크기를 가져와서 메모리에 올리고 해당 메모리의 주소를 반환한다

  mlx_put_image_to_window(mlx_ptr, win_ptr, img, 0, 0);

  이미지를 받아서 띄울 포인터들을 인자로 받고 윈도우 안에서의 좌표를 지정해서 해당 윈도우에 띄워준다




```

---

## 맵, .ber형식 파일

- 아래와 같이 예시로 하나 만들었다.

```
1111111111111
10010000000C1
1000011111001
1P0011E000001
1111111111111
```

- 지도는 0은 빈 공간, 1은 벽, C는 수집품, E는 맵의 출구, P는 주인공의 시작 지점 이렇게 5개의 문자열로 구성되어있다.
- 예시처럼 전체가 벽으로 둘러싸여 있어야 하며 출구, 수집품, 시작 지점은 반드시 하나 이상 있어야 한다. 만약 맵에 문제가 있다면 ”Error\n”와 직접 정한 에러 메시지를 출력하며 종료되어야 한다.

---
