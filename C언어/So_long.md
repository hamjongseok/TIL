# **๐ฆ So_long ๐ฆ**

## **๊ธฐ๋ณธ ๊ฐ๋**

---

- ์ถ๋ฐ์ ์์ ์์ํด์ ์์ดํ์ ๋จน๊ณ  ๋์ฐฉ์ ๊น์ง ์ต์ํ์ผ๋ก ????๊ฐ๋ ๊ฒ์ ๋ง๋ค๊ธฐ โญ๏ธ
- ์บ๋ฆญํฐ๊ฐ ์์ง์ผ ๋๋ง๋ค ์์ง์ธ ํ์๊ฐ ์์ ๊ธฐ๋ก๋์ด์ผ ํ๋ค โญ๏ธ
- W A S D๋ก ์บ๋ฆญํฐ ์ด๋
- ESC ๋๋ฅด๋ฉด ์ฐฝ์ด ๋ซํ๊ณ  ํ๋ก๊ทธ๋จ ์ข๋ฃ โญ๏ธ

  - wasd์ esc ๊ทธ๋ฆฌ๊ณ  ์ฐฝ ์๋จ์ ์ข๋ฃ ๋ฒํผ์ ๊ธฐ๋ฅ์ ์ด๋ป๊ฒ ๋ถ์ฌํ๋๊ฐ
  - miniLibX์ key๋ฅผ hook ํ  ์ ์๋ ๊ธฐ๋ฅ์ด ์๋ค. ํด๋น ํค์ ๊ธฐ๋ฅ์ ๋ถ์ฌํ๋ฉด ๋จ

- ์๋์ฐ์ ๋นจ๊ฐ ์ฐฝ๋ซ๊ธฐ ๋ฒํผ ๋๋ฅด๋ฉด ์ฐฝ์ด ๋ซํ๊ณ  ํ๋ก๊ทธ๋จ ์ข๋ฃ
- ์ธ์๋ก .ber ํ์ฅ์์ ๋งต์ ๋ฐ๋ ํ๋ก๊ทธ๋จ
  - ๋ด ๋ง์ ๋๋ก map.ber๋ฅผ ๋ง๋ค๋ฉด๋๋ค.
  - map ์ด ๋ค์ด์ฌ๋ 0, 1, E, C ์ด๋ฐ์์ผ๋ก ๋ค์ด์ค๋๋ฐ ์ด๋ค๊ฒ ๋ค์ด์ค๋์ง ํ๋จํด์ ์ถ๋ ฅํ๋ฉด๋๋ค.

---

## **๊ณผ์  ์์**

1.ย `.ber`ย ํ์ผ์ ์ธ์๋ก ๋ฐ์์ ์ฝ๊ธฐ (gnl)

- .ber ํ์ผ ์ฝ์ด์์ ํ๋จ, ๋ฌธ์ ํ๋๊ฐ ๋ฌด์์ธ์ง์ ๋ฐ๋ผ ์ด๋ฏธ์ง๋ฅผ ์๋ ฅํด์ฃผ๋ ๊ฒ์ด๋ค.

2. ์ด์ด๋ถ์ด๊ธฐ (join)

3. ๋งต์ ์ด์ค ํฌ์ธํฐ or ์ด์ฐจ์ ๋ฐฐ์ด์ ๋ด๊ธฐ (split)

์ด๊ฒ๋ ๋ชจ๋ฆ

4. ์ ํจ์ฑ ๊ฒ์ฌ

5. ๊ฐ ์นธ์ ๋ค์ด๊ฐ ์ด๋ฏธ์ง ํฌ๊ธฐ \* ์นธ ๊ฐ์ ํฌ๊ธฐ์ ์๋์ฐ, ์ด๋ฏธ์ง ์์ฑ

6. ๋งต ๋ฃจํ ๋๋ฉด์ ์ด๋ฏธ์ง ๋ฐ์ดํฐ ์ฐ๊ธฐ

---

- Minilibx๋?
  - MiniLibX๋ X-Window ๋ฐ Cocoa์ ๋ํ ์ง์ ์์ด๋ ํ๋ฉด์์ ๋ฌด์ธ๊ฐ๋ฅผ ๊ทธ๋ฆฌ๊ธฐ์ํ ๊ธฐ๋ณธ์ ์ธ ๊ทธ๋ํฝ ๋ผ์ด๋ธ๋ฌ๋ฆฌ์ด๋ค.
  - ๊ฐ๋จํ ์ฐฝ ์์ฑ, ๊ทธ๋ฆฌ๊ธฐ ๋๊ตฌ, ์ด๋ฏธ์ง ๊ธฐ๋ฅ ๋ฐ ์ด๋ฒคํธ ๊ด๋ฆฌ ์์คํ์ ์ ๊ณตํ๋ค.

---

# Mlx ํจ์

## Mlx ์ด๊ธฐํํ๊ธฐ

```c
#include <mlx.h>

int main(void)
{
	void *mlx_ptr;

	mlx_ptr = mlx_init();
	return (0);
}

mlx_ptr์ mlx_init()ํจ์๊ฐ ๋ฆฌํดํ๋ ์ฃผ์๋ฅผ ๊ฐ๋ฆฌํค๊ฒ ๋๋ค.

mlx_init()ํจ์๋ ๋์คํ๋ ์ด์ ์ฐ๋ฆฌ์ ํ๋ก๊ทธ๋จ์ ์ฐ๊ฒฐ์์ผ์ฃผ๋ ์ด๊ธฐํ ํจ์์ด๋ค.
```

## window์ฐฝ ์์ฑํ๊ธฐ

```c
win_ptr = mlx_new_window(mlx_ptr, 500, 500, "Hellow World!");

mlx_ptr : mlx_init์ด ๋ฐํํ ์ฐ๊ฒฐ ์๋ณ์
size_x : ์ฐฝ์ ๊ฐ๋ก ์ฌ์ด์ฆ
size_y : ์ฐฝ์ ์ธ๋ก ์ฌ์ด์ฆ
title : ํ์ดํ ๋ฐ์ ํ์๋  ๋ฌธ์์ด

```

- ์ด๊ธฐํ ํ์ง ์์ mlx_ptr์ด mlx_new_windowํจ์๋ก ์ ๋ฌ๋๋ค๋ฉด segfault๋ฅผ ๋ฐ์ํ๋ค.
- ํจ์๋ ์ฐฝ์ ์์ฑํ๋ ๊ฒ ๊น์ง๋ง ์๋ํ๊ณ  ์ค์ ๋ก ๋ชจ๋ํฐ์์ ์ฐฝ์ ๋์ฐ์ง ์๋๋ค. mlx_loop ํจ์๊ฐ ์ค์ ๋ก ๋ชจ๋ํฐ์์ ์ฐฝ์ ๋์ฐ๋ ์ญํ ์ ํด์ค๋ค.

```
int mlx_loop(void *mlx_ptr)

mlx_ptr :  ๋์คํ๋ ์ด์ ์ฐ๊ฒฐ๋์ด ์๋ mlx_ptr
return value : no return
```

- ๋ง์ง๋ง์ ์ด๊ฑธ ์ณ์ค์ผ ํ๋ก๊ทธ๋จ์ด ์ข๋ฃํ์ง ์๊ณ  ๊ณ์ ๋์๊ฐ๋ค.

## ํค Hook

```
int mlx_hook(void *win_ptr, int x_event, int x_mask, int (*func)(), void *param)

์๋์ฐ ์๋ณ์
X11 event
x_mask(mac์์  ๋ฏธ์ฌ์ฉ์ผ๋ก 0 ์๋ ฅ)
ํธ์ถํ  ํจ์ ํฌ์ธํฐ(๋๋ฆฐ ํค์ ์ฐฝ์์ ๋๋ฆฐ ์ขํ ๋ฑ์ด ์ ๋ฌ๋จ)
ํจ์์ ์ ๋ฌํ  ํ๋ผ๋ฏธํฐ๋ฅผ ์ธ์๋ก ๋ฐ๋ ํจ์

```

MAC OS์ ํค๋ณด๋ ์ฝ๋์ด๋ค.

```c
#define X_EVENT_KEY_PRESS 2 // mlx_hook ํจ์์ ๋๋ฒ์งธ ์ธ์
#define X_EVENT_KEY_RELEASE 3 // x_event์ ๋ค์ด๊ฐ๋ ๊ฐ , ์ด๊ฒ ์์์ด์ผ ํ๋์ง ๋ชจ๋ฅด๊ฒ ๋ค.

#define KEY_W 13
#define KEY_A 0
#define KEY_S 1
#define KEY_D 2
#define KEY_ESC 53 // MAC OS์ ํค๋ณด๋ ์ฝ๋ ๋ค์ด๋ค.


typedef struct  s_param // ํค ๊ฐ์ ์๋ ฅ๋ฐ๊ณ  ์ ํด์ง ๋์์ ์ํํ๋์ง ์ฌ๋ถ๋ฅผ ํ๋จํ๊ธฐ ์ํด ์ ์ธ
{
    int x; //x๊ฐ
    int y; //y๊ฐ
}   t_param;

void param_init(t_param *param) // ๊ตฌ์กฐ์ฒด param ์ด๊ธฐํ ํจ์
{
    param->x = 0;
    param->y = 0;
}

int key_press(int keycode, t_param *param) //์ด๋คํค ๋๋ ธ๋์ง ํ๋จํ๊ณ , ์ ์๋ ํ๋์ ์ํํ๋ ํจ์
{
    if (keycode == KEY_W) // W ํค๋ฅผ ๋๋ฅด๋ฉด param.x๊ฐ์ด 1 ์ฆ๊ฐ์๋๋ค.
        param->x++;
    else if (keycode == KEY_S) // S ํค๋ฅผ ๋๋ฅด๋ฉด param.x๊ฐ์ด 1 ๊ฐ์์๋๋ค.
        param->x--;
    else if (keycode == KEY_A) // A ํค๋ฅผ ๋๋ฅด๋ฉด param.y ๊ฐ์ด 1 ์ฆ๊ฐํ๋ค.
        param->y++;
    else if (keycode == KEY_D) // D ํค๋ฅผ ๋๋ฅด๋ฉด param.y๊ฐ์ด 1 ๊ฐ์ํ๋ค.
        param->y--;
    else if (keycode == KEY_ESC) //ESCํค๋ฅผ ๋๋ฅด๋ฉด ํ๋ก๊ทธ๋จ ์ข๋ฃ
        exit(0);
    printf("(x,y): (%d, %d)\n", param->x, param->y); //param์ ๊ฐ ํ์ธ
    return (0);

```

```c

#define X_EVENT_KEY_PRESS 2 // mlx_hook ํจ์์ ๋๋ฒ์งธ ์ธ์
#define X_EVENT_KEY_RELEASE 3

x_event์ X11 events๋ผ๊ณ  mlx์ ๋ฑ๋ก๋ ์ด๋ฒคํธ์ ๋ฒํธ๋ค. ๋ฒํธ์ ๋์๋๋ ์ด๋ฒคํธ๋ฅผ ํํนํ๋ค.

x11 events:
02: KeyPress
03: KeyRelease
```

---

## MAKEFILE

---

## ์ด๋ฏธ์ง

- xpmํ์ฅ์๋ก ๋ณํํ mlxํจ์๋ฅผ ์ด์ฉํด์ ๋งต์ ๋์ด๋ค.
- mlx_xpm_file_to_image์ mlx_put_image_to_window ์ ํ์ฉ

```c

  img = mlx_xpm_file_to_image(mlx_ptr, "./images/wall.xpm", &img_width, &img_height);

  mlxํฌ์ธํฐ, ํ์ผ ์ฃผ์, ๊ฐ๋ก ์ธ๋ก ํฌ๊ธฐ๋ฅผ ๊ฐ์ ธ์์ ๋ฉ๋ชจ๋ฆฌ์ ์ฌ๋ฆฌ๊ณ  ํด๋น ๋ฉ๋ชจ๋ฆฌ์ ์ฃผ์๋ฅผ ๋ฐํํ๋ค

  mlx_put_image_to_window(mlx_ptr, win_ptr, img, 0, 0);

  ์ด๋ฏธ์ง๋ฅผ ๋ฐ์์ ๋์ธ ํฌ์ธํฐ๋ค์ ์ธ์๋ก ๋ฐ๊ณ  ์๋์ฐ ์์์์ ์ขํ๋ฅผ ์ง์ ํด์ ํด๋น ์๋์ฐ์ ๋์์ค๋ค




```

---

## ๋งต, .berํ์ ํ์ผ

- ์๋์ ๊ฐ์ด ์์๋ก ํ๋ ๋ง๋ค์๋ค.

```
1111111111111
10010000000C1
1000011111001
1P0011E000001
1111111111111
```

- ์ง๋๋ 0์ ๋น ๊ณต๊ฐ, 1์ ๋ฒฝ, C๋ ์์งํ, E๋ ๋งต์ ์ถ๊ตฌ, P๋ ์ฃผ์ธ๊ณต์ ์์ ์ง์  ์ด๋ ๊ฒ 5๊ฐ์ ๋ฌธ์์ด๋ก ๊ตฌ์ฑ๋์ด์๋ค.
- ์์์ฒ๋ผ ์ ์ฒด๊ฐ ๋ฒฝ์ผ๋ก ๋๋ฌ์ธ์ฌ ์์ด์ผ ํ๋ฉฐ ์ถ๊ตฌ, ์์งํ, ์์ ์ง์ ์ ๋ฐ๋์ ํ๋ ์ด์ ์์ด์ผ ํ๋ค. ๋ง์ฝ ๋งต์ ๋ฌธ์ ๊ฐ ์๋ค๋ฉด โError\nโ์ ์ง์  ์ ํ ์๋ฌ ๋ฉ์์ง๋ฅผ ์ถ๋ ฅํ๋ฉฐ ์ข๋ฃ๋์ด์ผ ํ๋ค.

---
