# **🦑 So_long 🦑**

## **기본 개념**

---

- 출발점에서 시작해서 아이템을 먹고 도착점까지 최소한으로 ????가는 게임 만들기❌
- 캐릭터가 움직일 때마다 움직인 횟수가 쉘에 기록되어야 한다❌
- W A S D로 캐릭터 이동❌
- ESC 누르면 창이 닫히고 프로그램 종료 ⭕️

  - wasd와 esc 그리고 창 상단의 종료 버튼에 기능을 어떻게 부여하는가
  - miniLibX에 key를 hook 할 수 있는 기능이 있다. 해당 키에 기능을 부여하면 됨

- 윈도우의 빨간 창닫기 버튼 누르면 창이 닫히고 프로그램 종료❌
- 인자로 .ber 확장자의 맵을 받는 프로그램❌
  - 내 마음 대로 map.ber를 만들면된다.
  - ❌❌❌❌❌맵이 될수 없는 에러사항이 있으니 잘처리해줘야한다????????????
  - map 이 들어올때 0, 1, E, C 이런식으로 들어오는데 어떤게 들어오는지 판단해서 출력하면된다.

---

## **과제 순서**

1. `.ber` 파일을 인자로 받아서 읽기 (gnl)

- .ber 파일 읽어와서 판단, 문자 하나가 무엇인지에 따라 이미지를 입력해주는 것이다.

2. 이어붙이기 (join)

3. 맵을 이중 포인터 or 이차원 배열에 담기 (split)

이것도 모름

4. 유효성 검사

5. 각 칸에 들어갈 이미지 크기 \* 칸 개수 크기의 윈도우, 이미지 생성

6. 맵 루프 돌면서 이미지 데이터 쓰기

---

- Minilibx란?
  - MiniLibX는 X-Window 및 Cocoa에 대한 지식 없이도 화면에서 무언가를 그리기위한 기본적인 그래픽 라이브러리이다.
  - 간단한 창 생성, 그리기 도구, 이미지 기능 및 이벤트 관리 시스템을 제공한다.

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
}

여기서 왜 W에는 x를 더하고 S는 빼고 A는 더하고 D는 y를 빼는지 모르겠음

2차원 배열 특성때매 W랑 s를 y로 두면 좌우로 갔던거같다.
알아보기 ❌❌❌❌❌❌
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

## 2. va_start

```c
va_start(ap, 고정인수)
```

- va_start는 위에서 선언한 va_list 타입의 ap를 초기화 해주는 매크로이다.
- va_start를 통해 첫 번째 가변 인자의 주소를 ap가 참조할 수 있도록 만들어준다.
- 실제 코드를 보면 va_list 주소값에다가 고정인수 크기를 더한 위치로 ap를 초기화한다.
- 초기화하는이유는 ap는 가변함수에 들어오는 고정인수 다음부터 위치되어야하기때문

```c
#define va_start(ap, v)
 ( (ap) = (va_list)_ADDRESSOF(v) + _INTSIZEOF(v) )

va_start(ap, *fmt)
=> fmt 다음 가변인자 첫 주소를 가리키게한다.

```

- 가변인수를 가져올수있도록 포인터를 설정한다.

![](https://dojang.io/pluginfile.php/641/mod_page/content/30/unit66-1.png)

- 출처 코딩도장

---

## 3. va_arg

- 가변 인수를 실제로 읽는 명령이다.
- ap포인터가 위치한 부분의 데이터를 읽어 반환한다.
  그다음에 ap포인터를 타입길이만큼 뒤로 옮기기 때문에 그다음 값이 이어서 출력될수있다.

```c
단 ap번지에 있는 값이 어떤 타입인지를 지정해야 이매크로가 값을 제대로 읽을수 있으므로
두번째 인수로 읽고자하는 값의 타입을 지정한다.

예를 들어 ap 위치의 있는 정수값을 읽고자한다면 va_arg(ap, int)를 호출하고
실수 값을 읽고자 한다면 va_arg(ap, double)이라고 호출하면된다.
```

- 함수의 인수로는 값이 전달되는것이 정상인데 타입명이 어떻게 함수의 인수가 될수 있을까?
  - va_arg는 함수가 아니라 매크로 함수이기때문에 가능하다
  - va_arg의 두번째 인수는 내부적으로 sizeof 연산자와 캐스트 연산자로 전달되기 때문에
    타입명이 될수 있다.

```c
#define _crt_va_arg(ap,t)    ( *(t *)((ap += _INTSIZEOF(t)) - _INTSIZEOF(t)) )
```

- 더해서 주소값이 증가를 하고(그렇기 때문에 그다음 값이 이어진다) , 그다음 기존위치를 읽는것.
- type의 인수로는 char, float는 사용될 수 없다. int와 double로 대체

---

## 4. va_end

- va_list 를 널 , 0으로 초기화 한다. 다끝났다라는 뜻이다.
- 이함수는 가변인수를 다 읽은 후 뒷정리를 하는데 별다른 동작은 하지않으며
  실제로 없어 아무 지장이없다고 한다.
- 이 명령이 필요한 이유는 호환성때문인데 플랫폼에 따라서는 가변 인수를 읽은 후에 뒷처리를 하는 경우도있기 때문이다. 관례적으로 넣는것이 좋다.
