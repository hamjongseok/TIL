# **๐Born2beroot๐**

## **sudo**

- Super User Do์ ์ค์๋ง
- UNIX์์๋ root๊ณ์ ๋ง์ด ๋ชจ๋  ๋ช๋ น์ ์คํ, ํน์ ํ ์ค์์์์ ์ํํ ์์๋ค.
- sudo๋ช๋ น์ด๋ฅผ ํตํด ๋ค๋ฅธ ์ผ๋ฐ ์ฌ์ฉ์๊ฐ ์ผ๋ถ ๋ช๋ น์ ์คํํ๊ณ  ์์คํ ์์์ ์ํํ  ์ ์๋๋ก ํ์ฉํด์ค๋ค.

---

```c
sudo ๊ด๋ จ ๋ช๋ น์ด

dpkg -l sudo (์ค์น์ฌ๋ถ ํ์ธ)

apt install sudo (์๋์ค์น)

su - (root๊ณ์ ์ผ๋ก ์ด๋)

sudo (๋ช๋ น์ด)
์ผ๋ฐ์ ์ ๊ฐ root๊ถํ์ผ๋ก ๋ช๋ น์ด ์คํ

su (๊ณ์ ๋ช)
ํ์ฌ ์ ์ ๋ฅผ ๋ก๊ทธ์์ ํ์ง์์ ์ฑ๋ก ๋ค๋ฅธ ์ฌ์ฉ์ ๊ณ์ ์ผ๋ก ์ ํ

visudo (sudoerํ์ผ ์ ๊ทผ)

```

---

### subject ํญ๋ชฉ

- ๋น๋ฐ๋ฒํธ ์ค๋ฅ๋ 3๋ฒ์ผ๋ก ์ ํ๋ฉ๋๋ค. โญ๏ธ

  - `passwd_tries=3`

- sudo๋ฅผ ์ฌ์ฉํ  ๋, ์๋ชป ๋ ์ํธ๋ก ์ธํ ์ค๋ฅ๊ฐ ๋ฐ์ํ  ๊ฒฝ์ฐ ์ปค์คํ ๋ฉ์์ง๋ฅผ ํ์ํฉ๋๋ค. โญ๏ธ

  - `badpass_message=""`
  - Defaults authfail_message="์ํ๋ ์๋ฌ๋ฉ์ธ์ง" #๊ถํ ํ๋ ์คํจ ์ ์ถ๋ ฅ (sudo ์ธ์ฆ ์คํจ ์,3๋ฒ์ ๋น๋ฒ ํ๋ฆด๊ฒฝ์ฐ)

- sudo๋ฅผ ์ฌ์ฉํ  ๋์ ๋ชจ๋  ์์ถ๋ ฅ ๋์์ ๊ธฐ๋ก๋์ด์ผ ํฉ๋๋ค. ๋ก๊ทธ ํ์ผ์ย `/var/log/sudo/`ย ํด๋์ ์ ์ฅ๋ฉ๋๋ค. โญ๏ธ
  - `iolog_dir="/var/log/sudo/"` (๋ก๊ทธ ์ ์ฅํ  ๊ฒฝ๋ก)
- sudo๋ฅผ ์ด์ฉํ action๋ค์ input ๊ณผ output์ด archived(๋ชจ์ฌ์์ด์ผํจ)โญ๏ธ

  - Defalt log_input : sudo๋ฅผ ํตํด ์๋ ฅ๋ input์ ๋ก๊ทธ์ ๊ธฐ๋ก๋๋ค.
  - Defalt log_output : sudo๋ฅผ ํตํด ์๋ ฅ๋ output์ ๋ก๊ทธ์ ๊ธฐ๋ก๋๋ค

  ```c
  log ํ์ผ์ด๋ ?
  - ์ปดํจํฐ์ ๋ชจ๋  ์ฌ์ฉ๋ด์ญ์ ๊ธฐ๋กํ๊ณ  ์๋ ํ์ผ์ ๋งํ๋ค.
  - ํดํน ๋ฑ์ ์ฌ๊ฑด์ด ๋ฐ์ํ์๋, ๋ก๊ทธํ์ผ์ ๋ถ์ํ์ฌ ์ฌ๊ฑด์ ์์ธ์ ํ์ํ๋ค.
  ```

- ๋ณด์ ๋ฌธ์  ๊ด๋ จํด์, TTY ๋ชจ๋๋ฅผ ํ์ฑํํฉ๋๋ค.โญ๏ธ
  - `requiretty` (ttyํ๊ฒฝ์์๋ง sudo ๋ช๋ น์ด ์คํ๋  ์ ์๋๋ก ํ๋ค.)

```c
  TTY (Teletypewriter)

  ์ฝ์์ ํ ์ข๋ฅ๋ก Ctrl-Alt-F1 ~ F6 ํค์กฐํฉ์ผ๋ก ์ฌ์ฉํ ์์๋ OS ์์ ์ ๊ณตํ๋ ๊ฐ์์ฝ์ ์ด๋ค. ์ค์  ๋ฌผ๋ฆฌ์ ์ธ ์ฅ์น๊ฐ ์ฐ๊ฒฐ๋๊ฒ์ด ์๋๊ธฐ ๋๋ฌธ์ ์ปค๋์์ ํฐ๋ฏธ๋์ emulation ํ๋ค. TTYํ๋ฉด๊ฐ ์ด๋์ ALT+F1~F6์ด๋ฉฐ GUIํ๊ฒฝ ๋ณต๊ท๋ ALT+F7์ด๋ค.

์ถ์ฒ: https://booolean.tistory.com/666 [Boolean]

์ฝ์์ด๋ ?
CLI ํน์ CUI๋ผ๊ณ  ๋ถ๋ฆฌ๋ฉฐ ์ปดํจํฐ๋ฅผ ์ด์ฉํ๊ธฐ ์ํ ๋ชฉ์ ์ผ๋ก ํ์คํธ๋ฅผ ์ฌ์ฉ์์ ์ฃผ๊ณ  ๋ฐ๋ ๋ฐฉ์์ ์ธํฐํ์ด์ค๋ฅผ ๋งํ๋ค.

```

- ๋ณด์ ๋ฌธ์  ๊ด๋ จํด์, sudo์์ ์ฌ์ฉํ  ์ ์๋ ๊ฒฝ๋ก๋ ์ ํ๋ฉ๋๋ค. โญ๏ธ
  - `secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"`

```c
  sudo๋ช๋ น ์คํ ์ ํ์ฌ ๊ณ์ ์ ์์ด ์๋ ์๋ก์ด ์์ ์์ฑํ๊ณ  ๊ทธ ์์์ ๋ช๋ น์ ์คํํ๋๋ฐ, ์ด ๋ ๋ช๋ น์ ์ฐพ์ ๊ฒฝ๋ก๋ฅผ ๋์ดํ ํ๊ฒฝ๋ณ์์ธ PATH๊ฐ์ด secure_path

  shell ๋ช๋ น์ด๋ค์ PATH ํ๊ฒฝ๋ณ์์ ์ง์ ๋ ๊ฒฝ๋ก์์ ๋ฐ์ด๋๋ฆฌ ํ์ผ์ ์ฐพ๋๋ค.

 sudo ๊ถํ์ด ์๋ ์ฌ์ฉ์์ PATH ํ๊ฒฝ๋ณ์์ ์์ฑ์ฝ๋๋ก ์ธํ ๊ฒฝ๋ก๊ฐ ํฌํจ๋์ด ์์ด ํน์  ๋ช๋ น ์คํ์ ํด๋น ๊ฒฝ๋ก์์ ์์ฑ ํ์ผ์ด ์คํ๋  ๊ฒฝ์ฐ ์ ์ ๊ฐ sudo๋ฅผ ํตํด ์์คํ ์ ๋ฐ์ ๋ํ ๊ถํ์ ๋ถ์ฌ๋ฐ์ ์ฑ ํด๋น ๋ช๋ น์ ์คํํ๋ค๋ฉด ์์คํ์ ํฐ ๋ฌธ์ ๊ฐ ์๊ธธ ๊ฒ์ด๋ค.

์ด๋ฌํ ์ํฉ์ ๋ฐฉ์งํ๊ธฐ ์ํด sudo ๊ฐ ์คํ๋๋ ๊ฐ์ ์์์ ๋ช๋ น์ด์ ๋ฐ์ด๋๋ฆฌ ํ์ผ ๊ฒฝ๋ก๋ฅผ secure_path ๋ก ์ ํํ๋ ๊ฒ์ด๋ค.
```

---

## Group

- ์ด ์ฌ์ฉ์๋ย user42ย ์ย sudoย ๊ทธ๋ฃน์ ์ํด์ผ ํฉ๋๋ค โญ๏ธ
  - groupadd user42 ๋ช๋ น์ด๋ฅผ ํตํด user42๊ทธ๋ฃน ์ถ๊ฐ
  - usermod -aG sudo,user42 <์ฌ์ฉ์์ด๋ฆ> ๋ช๋ น์ด๋ฅผ ํตํด ํด๋น ๊ทธ๋ฃน์ ์ ์ ๋ฅผ ์ถ๊ฐ

```c
G ์ต์:
G์ต์๋ง ๋ถํ ์ํ์์ ๊ทธ๋ฃน ์ค์  ์, ๋ช๋ น์ด์ ๋์ด๋ ๊ทธ๋ฃน๋ง ์ถ๊ฐ๊ฐ ๋๋ฉฐ ๋ช๋ น์ด์ ๋์ด๋์ด ์์ง ์์ง๋ง ์ ์ ๊ฐ ์ํด์๋ ๊ทธ๋ฃน์ ์ ๋ถ ํํด๋๋ค.

a ์ต์:
G์ต์์์๋ง ํจ๊ป ์ฐ์ผ ์ ์๊ณ , G์ต์๋ง ๋ถ์์ ๋์ ๋ฌ๋ฆฌ, ์ ์ ๊ฐ ์ํด์์ง๋ง ๋ช๋ น์ด์ ๋์ด๋์ด์์ง ์๋ ๊ทธ๋ฃน์ ๊ดํ์ฌ ํํด์ฒ๋ฆฌ ๋์ง ์๋๋ค.

"sudo deluser ์ฌ์ฉ์๋ช ๊ทธ๋ฃน๋ช"์ ํตํด ๊ทธ๋ฃน์์ ์ฌ์ฉ์๋ฅผ ์ ๊ฑฐํ  ์ ์๋ค.

"sudo userdel -r ์ฌ์ฉ์๋ช" ํตํด ์ฌ์ฉ์ ์ ๊ฑฐ ๊ฐ๋ฅ.
```

- id jham (์ด๋ ๊ทธ๋ฃน์ ์ํด์๋์ง ๋์จ๋ค.)

---

## `UFW`

- ๋ฐฉํ๋ฒฝ์ด๋ ?
  - ์ธ๋ถ ์ฌ์ฉ์(WAN)๋ค์ด ๋ด๋ถ ๋คํธ์ํฌ(LAN)์ ์ ๊ทผํ์ง ๋ชปํ๋๋ก ํ๋ ์ผ์ข์ ๋ด๋ถ ๋คํธ์ํฌ ๋ฐฉ์ด๋๊ตฌ์ด๋ค.
  - ๋ฐฉํ๋ฒฝ์ ์ ๋ขฐํ  ์ ์๋ ๋ด๋ถ ๋คํธ์ํฌ, ์ ๋ขฐํ  ์ ์๋ ์ธ๋ถ ๋คํธ์ํฌ ๊ฐ์ ์ฅ๋ฒฝ์ ๊ตฌ์ฑํ๋ค.
  - ์๋ก ๋ค๋ฅธ ๋คํธ์ํฌ๋ฅผ ์ง๋๋ ๋ฐ์ดํฐ๋ฅผ ํ์ฉ ๋๋ ๊ฑฐ๋ถ ํ๊ฑฐ๋ ๊ฒ์ด ๋๋ ์์ ํ๋ ํ๋์จ์ด ๋๋ ์ํํธ์จ์ด๋ค.
- UFW ?
  - Uncomplicated Firewall์ ์ฝ์
  - Debian ๊ณ์ด ๋ฐ ๋ค์ํ ๋ฆฌ๋์ค ํ๊ฒฝ์์ ์๋๋๋ ์ฌ์ฉํ๊ธฐ ์ฌ์ด ๋ฐฉํ๋ฒฝ ๊ด๋ฆฌ ํ๋ก๊ทธ๋จ
  - UTF๋ ์์ฌ์ด ์กฐ์์ผ๋ก iptable ๋ฐ ์ฌ์ฌ ์ค์ ์ ๋์ ํด์ค๋ค.(Uncomplicated: ๋ณต์กํ์ง ์์) ๋ฐ๋น์์ ๊ธฐ๋ณธ ๋ฐฉํ๋ฒฝ์ iptable์ด๋ค.
  - iptable์ด๋?
    - ์์คํ๊ด๋ฆฌ์๊ฐ ๋ฆฌ๋์ค ์ปค๋ ๋ฐฉํ๋ฒฝ์ด ์ ๊ณตํ๋ ํ์ด๋ธ๊ณผ ๊ทธ๊ฒ๋ค์ ์ ์ฅํ๋ ์ฒด์ธ, ๊ท์น๋ค์ ๊ตฌ์ฑํ  ์ ์๊ฒ ํด์ฃผ๋ ์ฌ์ฉ์ ๊ณต๊ฐ ์์ฉํ๋ก๊ทธ๋จ

```
ํ๊ฐ๋ ์ฌ์ฉํ๋ ๋ช๋ น์ด

ufw enable: ๋ฐฉํ๋ฒฝ ํ์ฑํ

ufw status: ๋ฐฉํ๋ฒฝ ์ํ๋ฅผ ํ์ธ

ufw delete (๊ท์น ๋ฒํธ): ์ ์๋ ํน์  ๋ฒํธ์ ๊ท์น ์ ๊ฑฐ

ufw allow (ํฌํธ๋๋ฒ): ํน์  ํฌํธ๋๋ฒ ์ ์ ํ์ฉ

ufw deny (ํฌํธ๋๋ฒ): ํน์  ํฌํธ๋๋ฒ ์ ์ ์ ํ
```

---

## SSH

- Secure Shell Protocol
- ์๊ฒฉ ํธ์คํธ์ ์ ์ํ๊ธฐ ์ํด ์ฌ์ฉ๋๋ ๋ณด์ ํ๋กํ ์ฝ
- ๋ํ์ ์ธ ์ฌ์ฉ

  - ๋ฐ์ดํฐ ์ ์ก (๊น ํธ์)
  - ์๊ฒฉ์ ์ด (aws๊ฐ์ ํด๋ผ์ฐ๋ ์๋น์ค)
  - ํฌํธํฌ์๋ฉ

- apt search openssh-server ๋ช๋ น์ด๋ฅผ ํตํด openssh๊ฐ ๊น๋ ค์๋์ง ํ์ธ.
  - ๊น๋ ค์์ง ์๋ค๋ฉด, apt install open ssh-server ๋ช๋ น์ด๋ก ์ค์น
- ๊น๋ ค์์ง ์๋ค๋ฉด, apt install open ssh-server ๋ช๋ น์ด๋ก ์ค์น
- sudo vim /etc/ssh/sshd_config ๋ช๋ น์ด๋ฅผ ํตํด ssh์ค์ ์ ๋ณ๊ฒฝ
- PermitRootLogin ๋ถ๋ถ์ no๋ก ๋ฐ๊พผ๋ค. ํด๋น ์ต์์ ํตํด ์ธ๋ถ์์ root๋ก ๋ก๊ทธ์ธํ๋ ๊ฒ์ ๋ง์ ์ ์๋ค.
- hostname -I
  - ๊ฐ์ ip ํ์ธ
- ํฌํธํฌ์๋ฉ
  - ssh -p 4242 jham@192.168.56.1

---

## ๋น๋ฐ๋ฒํธ ์ ์ฑ

chage -l <์ฌ์ฉ์>๋ฅผ ํตํด ํ์ฌ ์ฌ์ฉ์์ ์ํธ์ ๋ณด๋ฅผ ์ ์ ์๋ค.

๊ธฐ๋ณธ ์ ์ฑ

- Last password change (-d) : ๋ง์ง๋ง ํจ์ค์๋ ๋ณ๊ฒฝ์ผ
- Password expires : ์ํธ ๋ง๋ฃ์ผ
- Password inactive(-I (๋๋ฌธ์i)) : ๋นํ์ฑํ ์ ์๊ธฐ๊ฐ
- Account expires(-E) : ๊ณ์  ๋ง๋ฃ์ผ
- Minimum number .... (-m) : ํจ์ค์๋ ๋ณ๊ฒฝ ํ ์ต์ ์ฌ์ฉ ๊ธฐ๊ฐ, ์ฆ ์ต์ ์๋ฌด ์ฌ์ฉ์ผ
- Maximum number .... (-M) : ํจ์ค์๋ ๋ณ๊ฒฝ ํ ๋ณ๊ฒฝ ์์ด ์ฌ์ฉ๊ฐ๋ฅํ ์ต๋ ์ผ ์
- Number of days of warning ... (-W) : ํจ์ค์๋ ๋ง๋ฃ ์  ๊ฒฝ๊ณ ๋ฉ์ธ์ง๋ฅผ ๋ณด๋ผ ์ผ ์

- ์๋ธ์ ํธ์์ ์๊ตฌ์ฌํญ

1. password ๋ 30์ผ๋ง๋ค ๋ง๋ฃ๋์ด์ผํ๋ค. -M 30
2. ๋น๋ฐ๋ฒํธ ์ต์ ์ฌ์ฉ์ผ์ด 2์ผ ์ด๋ค (๋น๋ฐ๋ฒํธ ๋ณ๊ฒฝํ 2์ผ์ด ์ง๋์ผ ๋ค์๋ณ๊ฒฝ ๊ฐ๋ฅ) -m 2
3. ์ ์ ๋ ๋น๋ฐ๋ฒํธ ๋ง๋ฃ 7์ผ์ ์ ๊ฒฝ๊ณ  ๋ฉ์ธ์ง๋ฅผ ๋ฐ์์ผ ํ๋ค. -W 7

- sudo chage -M 30 -m 2 -W 7 jham ์ผ๋ก ์ค์  ์๋ฃ

์ ์ฒด ์ ์ฑ ๋ณ๊ฒฝ

- ์ ๋ฐฉ๋ฒ์ ๋์ ๊ณ์ ๋ง ์ ์ฑ์ ๋ณ๊ฒฝ์ํค๊ณ  ์ด์  ์๋ก ๋ง๋ค์ด์ง user์๋ ๊ฐ์ ์ ์ฑ์ด ์ ์ฉ๋๋ ์ ์ฒด ์ ์ฑ์ ๋ณ๊ฒฝํด์ผํ๋ค.
- vi /etc/pam.d/common-password ๋ฅผ ํตํด ํ์ฌ ํจ์ค์๋ ์ ์ฑ์ ํ์ธํ  ์ ์๋ค.
- ํจ์ค์๋ ์ ์ฑ ์ค์ ์ ์ํ ๋ชจ๋์ ์ค์น
- sudo apt install libpam-cracklib

```
๋น๋ฐ๋ฒํธ๋ ์ต์ 10์๋ฆฌ์ฌ์ผ ํ๋ค. minlen=10

์์ด ๋๋ฌธ์ + ์ซ์๋ ๊ผญ ํฌํจํ๊ณ  ์์ด์ผ ํ๋ค. ucredit์ซ์, decredit์ซ์

3๊ฐ ์ด์์ ์ฐ์๋ ๋์ผํ ๋ฌธ์๋ฅผ ๊ฐ์ง๋ฉด ์๋๋ค. maxrepeat = 3

๋น๋ฐ๋ฒํธ๋ ์ฌ์ฉ์์ ์ด๋ฆ์ ํฌํจํ๋ฉด ์๋๋ค. reject_username

๋น๋ฐ๋ฒํธ๋ ์ด์ ์ ๋น๋ฐ๋ฒํธ์ ๋ค๋ฅธ ์ต์ 7๊ธ์๋ฅผ ๊ฐ์ ธ์ผ ํ๋ค. difok = 7

root password๋ ์ด ์ ์ฑ์ ๋ฐ๋ผ์ผํ๋ค. enforce_for_root

```

- `retry=N`ย : ์ํธ์๋ ฅ์ Nํ๋ก ์ค์ 
- `minlen=N`ย : ์ํธ์ ์ต์ ๊ธธ์ด๋ N
- `difok=N`ย : ๊ธฐ์กด ํจ์ค์๋์ ๋ฌ๋ผ์ผํ๋ ๋ฌธ์ ์ N
- `ucredit=-N`ย : ๋๋ฌธ์ N๊ฐ ์ด์
- `lcredit=-N`ย : ์๋ฌธ์ N๊ฐ ์ด์ -1
- `decredit=-N`ย : ์ซ์ N๊ฐ ์ด์ -1

(N < 0)
์ ํจ์ค์๋์ ์์ด์ผ ํ๋ ๋๋ฌธ์ ์ต์ ๊ฐ์.

- `reject_username`ย : ์ฌ์ฉ์์ ์ด๋ฆ์ด ๊ทธ๋๋ก ํน์ ๋ค์งํ ํจ์ค์๋์ ์๋์ง ๊ฒ์ฌ
- `enforce_for_root`ย : root์ฌ์ฉ์๊ฐ ํจ์ค์๋๋ฅผ ๋ฐ๊พธ๋ ค ํ  ๋์๋ ์ ์กฐ๊ฑด ์ ์ฉ
- `maxrepeat=N`ย : ๊ฐ์ ๋ฌธ์๊ฐ N๋ฒ ์ด์ ์ฐ์ํด์ ๋์ค๋์ง ๊ฒ์ฌ

---

## hostname

- hostnamectl ๋ช๋ น์ด๋ฅผ ํตํด hostname์ ํ์ธํ  ์ ์๋ค.
- sudo vi /etc/hostname ๋ค์ด๊ฐ์ ๋ฐ๊ฟ, ๊ป๋ค๊ฐ ์ผ์ผํจ

## LVM

- lsblk ๋ช๋ น์ด๋ก ํํฐ์์ ํ์ธ ํ  ์ ์๋ค.
- mandatory ํํธ ์์์ ๋น๊ต

LVM์ด๋ ?

- Logical Volume Manager
- ์ด๋ฆ ๋ป ๊ทธ๋๋ก Logical(๋ผ๋ฆฌ์ ์ธ) Volume(๊ณต๊ฐ์) Manager(๋ง๋ค๊ณ  ๊ด๋ฆฌ ํด์ฃผ๋ ํ๋ก๊ทธ๋จ์ด๋ค.
- ๋์คํฌ ํจ์จ ๊ด๋ฆฌ ๊ธฐ์ 
- ์ฌ์ฉ ์ด์ 
  - ์ฌ๋ฌ๊ฐ์ ๋์คํฌ ๊ณต๊ฐ์ ํฉ์ณ์ ํ๋์ธ ์ ์ฌ์ฉํ๊ธฐ ์ํด
  - ์ฌ์ฉํ๊ธฐ ์ ๋งคํ ๊ณต๊ฐ์ ๋์คํฌ ํํฐ์๋ค์ ํ์ฉํ๊ธฐ ์ํด
  - ๊ธฐ์กด์ ์ฌ์ฉ์ค์ธ ๋์คํฌ์ ๊ณต๊ฐ์ ํ์ฅํ  ์ ์๊ธฐ ๋๋ฌธ์
- ํํฐ์์ด๋?
  - ์ด๋ค ํ๋์ ๋ฌด์ธ๊ฐ๋ฅผ ์ฌ๋ฌ๊ฐ๋ก ๋๋๋ ๊ฐ๋
- LVM ?
  - ์ฌ๋ฌ ๋์คํฌ ๊ณต๊ฐ, ์งํฌ๋ฆฌ ๊ณต๊ฐ์ ํฉ์ณ์ ํ๋๋ก ๋ง๋๋ ๊ฒ
  - ํ๋ฒ ํํฐ์์ ๋๋๋ฉด ์๋ก ์ฉ๋์ ์ฃผ๊ณ  ๋ฐ์ ์ ์๋ค.
  - ํํฐ์์ ๋ผ๋ฆฌ์ ์ธ ๊ฐ๋(LVM)์ผ๋ก ๋๋๋ฉด, ์ฉ๋์ ์๋ก ์ฃผ๊ณ  ๋ฐ์ ์ ์๋ค.
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e2d603f4-b7a7-450d-a9fa-0f0e4f7fa152/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.13.22.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220314%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220314T041338Z&X-Amz-Expires=86400&X-Amz-Signature=0b8ecf4a32eb7f987849821cce3320595b9c353ff467e323d5d658288ee7ae07&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.13.22.png%22&x-id=GetObject)

## LVM ์ฉ์ด

- PV(Physical Volume)

  - LVM์์ ๋ธ๋ก ์ฅ์น๋ฅผ ์ฌ์ฉํ๋ ค๋ฉด PV๋ก ์ด๊ธฐํ๋ฅผ ํด์ผํ๋ค. ์ฆ, ํํฐ์๋ค์ LVM์์ ์ฌ์ฉํ  ์ ์๊ฒ ๋ณํํ๋๊ฒ
  - PV๋ ์ผ์ ํ ํฌ๊ธฐ์ PE(Pysyical Extent)๋ค๋ก ๊ตฌ์ฑ์ด ๋๋ค.

- PE((Physical Extent)
  - PV๋ฅผ ๊ตฌ์ฑํ๋ ์ผ์ ํ ํฌ๊ธฐ์ ๋ธ๋ก์ผ๋ก ๊ธฐ๋ณธํฌ๊ธฐ๋ 4MB
  - V(Logical Volume)์ LE(Logical Extent)๋ค๊ณผ 1:1๋ก ๋งตํ๋๋ค. ๊ทธ๋ ๊ธฐ์ ํญ์ PE์ LE์ ํฌ๊ธฐ๋ ๋์ผํ๋ค.
- PV๋ก ์ด๊ธฐํ์ํจ ๋ชจ์ต
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/988c7566-0423-4c93-9f6c-009db483b376/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.29.13.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220314%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220314T042925Z&X-Amz-Expires=86400&X-Amz-Signature=3b5156c1f6c8f30eed755597be8014cf45514207ccaa52aa68099e179bc87601&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.29.13.png%22&x-id=GetObject)
- VG(Volume Group)
  - PV๋ค์ ์งํฉ์ผ๋ก LV๋ฅผ ํ ๋นํ  ์ ์๋ ๊ณต๊ฐ์ด๋ค
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5640f21b-ea32-4204-8d28-510a675a82f8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.30.29.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220314%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220314T043103Z&X-Amz-Expires=86400&X-Amz-Signature=02a3d0ca3602378f7d0f0c1ad4336d799d2bf0ea6eca45eab4540a51235e0119&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.30.29.png%22&x-id=GetObject)
- LV(Logical Volume)
  - ์ฌ์ฉ์๊ฐ ์ต์ข์ ์ผ๋ก ๋ค๋ฃจ๊ฒ๋๋ ๋ผ๋ฆฌ์ ์ธ ์คํ ๋ฆฌ์ง
- LE(Logical Extent)
  - LV๋ฅผ ๊ตฌ์ฑํ๋ ์ผ์ ํ ํฌ๊ธฐ์ ๋ธ๋ก์ผ๋ก ๊ธฐ๋ณธํฌ๊ธฐ๋ 4MB์ด๋ค.
  - ํญ์ PE์ LE์ ํฌ๊ธฐ๋ ๋์ผํ๋ค.
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cb92bdfe-e3f1-43a5-8e89-ac7ab4ac21ee/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.32.24.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220314%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220314T043318Z&X-Amz-Expires=86400&X-Amz-Signature=161f90c2d089e49b5fb7f14c034a86b2845a95cc36a73af52a50055ae4e53f29&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.32.24.png%22&x-id=GetObject)
  - VG์์ ํ์์ ๋ฐ๋ผ LV๋ฅผ ๋ง๋ค์ด์ ์ฌ์ฉํ๋ค.

---

### cron

- ํน์ ํ ์๊ฐ์ or ํน์  ์๊ฐ๋ง๋ค ์ด๋ค ์์์ ์๋์ผ๋ก ์ํํ๊ฒ ํ๋ ๋ช๋ น์ด

crontab

- cron์์์ ์ค์ ํ๋ ํ์ผ
- cronํ๋ก์ธ์ค๋ /etc/crontab ํ์ผ์ ์ค์ ๋ ๊ฒ์ ์ฝ์ด ์์์ ์ํ
- sudo cat /etc/crontab

cron ์ค์  ๋ฐฉ๋ฒ

- sudo crontab -e
- \*/10 \* \* \* \* /monitoring.sh | wall : 10๋ถ๋ง๋ค root๊ถํ์์ "/monitoring.sh | wall" ์คํ
- \* \* \* \* sleep [ ]; command : ์ด๋จ์๋ก ์ปจํธ๋ก ํ๋ ค๋ฉด
- \* \* \* \* \* ๋ช๋ น์ด & sleep 30; ๋ช๋ น์ด

## monitoring.sh

- OS์ architecture ๋ฐ kernel version
  - printf "#Architecture: "
  - uname -srvmo
    - -s๋ ์ปค๋ ์ด๋ฆ, -r์ ์ปค๋๋ฆด๋ฆฌ์ฆ, -v๋ ์ปค๋ ๋ฒ์ , -m์ ์ํคํ์ณ, -o๋ os์ถ๋ ฅ
- physical(๋ฌผ๋ฆฌ์ ) processors ๊ฐ์
  - printf "#CPU physical : "
  - nproc --all
    - "nproc --all"์ ํตํด ์ค์น๋ ํ๋ก์ธ์์ ๊ฐฏ์๋ฅผ ์ถ๋ ฅ
- virtual(๊ฐ์) processors ๊ฐ์
  - printf "#vCPU : "
  - cat /proc/cpuinfo | grep processor | wc -l
    - ๊ฐ์ ํ๋ก์ธ์(vCPU)์ ๊ฐฏ์๋ฅผ ์ถ๋ ฅ
    - wc -l : ๋ผ์ธ์ ๋ณด์ฌ์ค
    - grep : ํ์คํธ ํ์ผ์์ ์ํ๋ ๋ฌธ์์ด์ด ๋ค์ด๊ฐ ํ์ ์ฐพ์ ์ถ๋ ฅํ๋ ๋ช๋ น์ด.
- ์๋ฒ์์ ์ฌ์ฉ ๊ฐ๋ฅํ RAM ๋ฐ ์ฌ์ฉ๋ฅ (%)

  - printf "#Memory Usage: "
  - free -m | grep Mem | awk '{printf"%d/%dMB (%.2f%%)\n", $3, $2, $3/$2 \* 100}'
    - // free ์ฌ์ฉ๊ฐ๋ฅํ ๋ฉ๋ชจ๋ฆฌํ์ธ
    - free๋ช๋ น์ด๋ ๋ฆฌ๋์ค ์์คํ์์ ๋ฉ๋ชจ๋ฆฌ์ ์ ์ฒด์ ์ธ ํํฉ์ ์ดํด๋ณผ ์ ์๋ ๋ช๋ น์ด
    - -m ์ต์์ ํตํด MB๋ก ๋จ์ ๋ณ๊ฒฝ
    - awk๋ฅผ ์ฌ์ฉํ์ฌ ์ ์ ํ ๊ฐ ๋์ถ

- ์๋ฒ์์ ์ฌ์ฉ ๊ฐ๋ฅํ ๋ฉ๋ชจ๋ฆฌ ๋ฐ ์ฌ์ฉ๋ฅ (%)
  - printf "#Disk Usage: "
  - df -BM -a | grep /dev/mapper/ | awk '{sum+=$3}END{print sum}' | tr -d '\n'
    - df ์ฌ์ฉ๊ฐ๋ฅํ ๋์คํฌ ์ฉ๋ ํ์ธ
    - -BM , MB๋ก ๋ณ๊ฒฝ(-m ๋ ๊ฐ๋ฅ ) -a , ๋ชจ๋(0์ธ๊ฒ๋ ๋ณด๊ธฐ)
    - '{sum+=$3}END{print sum}' ์ธ๋ฒ์งธ ํ๋์ ํฉ๊ณ์ฐ
    - tr -d '\n' ๊ฐํ ์ญ์ 
  - printf "/"
  - df -BM -a | grep /dev/mapper/ | awk '{sum+=$4}END{print sum}' | tr -d '\n'
  - printf "MB ("
  - df -BM -a | grep /dev/mapper/ | awk '{sum1+=$3 ; sum2+=$4}END{printf "%d", sum1 / sum2 \* 100}' | tr -d '\n'
  - printf "%%)\n"
- Cpu ์ฌ์ฉ๋

  - printf "#CPU load: "
  - mpstat | grep all | awk '{printf "%.2f%%\n", 100-$13}'
    - sysstat๋ฅผ ๋ค์ด๋ฐ์ mpstat ๋ช๋ น์ด๋ฅผ ์ฌ์ฉํ๋ฉด ์ฝ๊ฒ ํ์ฌ CPU์ ์ฌ์ฉ๋์ ์ ์ ์๋ค.
    - mpstat ๋ช๋ น์ด์์ ๋ง์ง๋ง ์ปฌ๋ผ์ ํ์ฉํ์ฌ ๊ฒฐ๊ณผ๋ฅผ ๋์ถ

- ๋ง์ง๋ง ๋ถํ๋ ์ง ๋ฐ ์๊ฐ
  - who -b | sed 's/^ \*system boot //g'
    - last reboot ๋ช๋ น์ด๋ฅผ ์ฌ์ฉํ๋ฉด ๋ง์ง๋ง์ผ๋ก ์ฌ๊ธฐ๋ํ ์๊ฐ์ด ์ธ์ ์ธ์ง ์ ๋ ฌํ์ฌ ์ถ๋ ฅํ๋ค.
    - who ๋ช๋ น์ด๋ ํ์ฌ ๋ด๊ฐ ์ด๋ค ์ฌ์ฉ์๋ก ์ ์์ ํ๋์ง ํ์ธํ๊ธฐ ์ํด ์ฌ์ฉํ  ์ ์๋ค.
    - -b ์ต์์ ์ฌ์ฉํ๋ฉด ๋ง์ง๋ง ์์คํ ๋ถํ ์๊ฐ์ ์ถ๋ ฅํ๋ค๋ ๋ป.
    - sed๋ ์ถ์ถํ๋ ๋ช๋ น์ด
- LVM์ด ํ์ฑ ์ํ์ธ์ง ์ฌ๋ถ
  - printf "#LVM use: "
  - if [ "$(lsblk | grep lvm | wc -l)" -gt 0 ] ; then printf "yes\n" ; else printf "no\n" ; fi
    - lsblk ๋ช๋ น์ด๋ฅผ ์ฌ์ฉํ๋ฉด ํ์ฌ ์ฅ์ฐฉ๋ ๋์คํฌ์ ์ฃผ์ ์ฌ์์ ํ์ธํ  ์ ์๋ค.
    - ๋ฆฌ๋์ค if๋ฌธ ํ์ฉ
- ํ์ฑ ์ฐ๊ฒฐ ์

  - printf "#Connections TCP : "
  - ss | grep -i tcp | wc -l | tr -d '\n'
  - ํต์ ํ๋ ์์ผ , ์๊ฒฉํ๋ฉด 1 ์๊ธด๋ค.

- ์ฌ์ฉ์ ์ ๋ณด ํ์ธ
  - printf "#User log: "
    - who | wc -l
- mac์ฃผ์ ํ์ธ

  - printf "#Network: IP "
  - hostname -I | tr -d '\n'
    - ip adress ํ์ธ;
  - printf " ("
  - ip link show | awk '$1 == "link/ether" {print $2}' | tr -d '\n'
    - //๋ชจ๋  ๋คํธ์ํฌ ์ธํฐํ์ด์ค์ ์ํ๋ฅผ ๊ด๋ฆฌํ๊ณ  ์ถ๋ ฅํจ
  - printf ")\n"

- sudo ํ๋ก๊ทธ๋จ ์คํ๋ ๋ช๋ น ์

  - printf "#Sudo : "
  - journalctl \_COMM=sudo | grep COMMAND | wc -l | tr -d '\n'

    - journalctl์ ์ฌ์ฉํ๋ฉด systemd-journald ๋ฐ๋ชฌ์ด ์์งํ ๋ชจ๋  ๋ก๊ทธ ์ ๋ณด๋ฅผ ๋ณผ ์ ์๋ค.
    - journalctl์ ์ฌ์ฉํ์ฌ ํน์  ๋ก๊ทธ๋ฅผ ๋ณด๊ณ ์ถ๋ค๋ฉด \_COMM=<ํน์ > ์ต์์ ์ถ๊ฐํ๋ฉด ๋๋ค.

  - printf " cmd\n"

- ๋ณธํฌ๋น ๋ฃจํธ ๋ 4์ 20์ผ๊น์ง push_swap ์ด๋์ ๋ ๊ตฌํ ๋๋ด๊ณ  ๋ง๊น์ง ํ๊ฐ ์งํ ๋ชฉํ
