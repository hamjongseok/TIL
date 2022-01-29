# **🌎Born2beroot🌎**

## **Subject**

---

- This project aims to introduce you to the wonderful world of virtualization.

## General guidelines

---

- Virtualbox or UTM 사용 가능
- 서버 셋업하기. CUI로 미니멈한 서버를 세팅
- 설치는 최소한으로 진행되어야 한다.(GUI 설치 금지!)
- OS로는 Debian의 최신 stable 버전이나 CentOS의 최신 stable 중 하나를 선택해라.
- CentOS 에서 kdump 셋업은 필요하지 않다. SElinux는 필수 AppArmor for Debian도 필수
- LVM를 사용해서 암호화된 파티션을 2개 이상 생성해야 한다.

---

![image description](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0b0587b6-306b-4f41-99c6-e61a69423256/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-01-29_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.05.02.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220129%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220129T034741Z&X-Amz-Expires=86400&X-Amz-Signature=8a62458682a19d2d563c8dbc888c4909c26a5d1c8c94ceddf9715931628b8c10&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-01-29%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252012.05.02.png%22&x-id=GetObject)

---

- aptitude와 apt 의 차이, SELinux 혹은 AppArmor이 무엇인지 알고 있어야 한다.
- 사용하는 운영체제에 대한 설명
- SSH 서비스는 4242 포트에서만 실행된다. 보안상의 이유로 SSH를 root로 사용해서 연결하는 것은 금지돤다.
- ssh가 어떻게 작동하는지 알고 있어야 한다.
- UFW 방화벽을 이용해야하고 4242포트만 열어놔야한다.
- 방화벽은 가상머신을 시작할때 작동해야한다. centOS에서 기본방화벽 대신에 UFW방화벽을 이용해야 한다. 설치하기 위해서는 DNF가 필요할듯
- 가상 머신의 `hostname`은 `[당신의 로그인]42` 형식이어야 합니다. 예시: `wil42`
- 강한 암호 폴리시를 구현해야합니다.
- 엄격한 규칙에 따라 `sudo`를 설치하고 구성해야 합니다.
- root 유저 외에도 `[당신의 로그인]`이 유저네임인 유저가 존재해야 합니다.
- 이 사용자는 `user42` 와 `sudo` 그룹에 속해야 합니다
- 평가 중에 새 유저를 생성해서 그룹에 할당해야 합니다.

- 강한 암호를 셋업하기 위해, 다음 요구 사항을 준수해야 합니다.

```c
1. password 는 30일마다 만료되어야한다.
2. 비밀번호 최소 사용일이 2일 이다 (비밀번호 변경후 2일이 지나야 다시변경 가능)
3. 유저는 비밀번호 만료 7일전에 경고 메세지를 받아야 한다.
4. 비밀번호는 최소 10자리여야 한다. 영어 대문자 + 숫자는 꼭 포함하고 있어야 한다. 3개 이상의 연속된 동일한 문자를 가지면 안된다.
5. 비밀번호는 사용자의 이름을 포함하면 안된다.
6. 비밀번호는 이전의 비밀번호와 다른 최소 7글자를 가져야 한다.
7. 당연히 root password는 이 정책을 따라야한다.
8. 구성 file을 셋팅한 후, 가상머신에 존재하는 모든 계정의 비밀번호를 바꿔야 한다. 루트계정 포함.
```

---

- Sudo 그룹은 다음에 요구되는 강력한 구성을 준수해야 합니다

```c
1. sudo를 이용한 인증은 3번의 시도로 제한한다.(비밀번호 틀리는거 3번까지 허용)
2. sudo 이용시 비밀번호 잘못 입력시, custom message(내맘대로) 가 보여야 한다.
3. sudo를 이용한 action들은 input 과 output이  archived(모여있어야함). 로그 파일은 /var/log/sudo/ 폴더에 저장
4. 보안적인 이유로 tty모드는 가능해야 한다.
5. 보안적인 이유로 the paths that can be used by sudo must be restricted.

    e.g. /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin


 결국 monitoring.sh라는 간단한 스크립트를 만들었을건데, bash로 실행 가능해야함
서버가 실행되고, 이 스크립트는 모든 터미널에 매 10분마다 몇 가지 정보를 표시해야 합니다. (wall을 참고하세요.)


OS 아키텍처와 커널 버전

물리적 프로세서의 수

가상 프로세서의 수

서버에서 사용가능한 RAM과 사용률(%로 표시)

서버에서 사용가능한 메모리와 사용률(%로 표시)

프로세서의 사용률(%)

마지막으로 재부팅된 날짜와 시각

LVM의 활성 여부

활성화 된 연결의 수

서버를 사용하는 유저의 수

서버의 IPv4 주소와 MAC 주소

`sudo` 프로그램으로 실행된 커맨드의 수
```

- 평가 중에, 스크립트가 어떻게 실행되는지 설명해야합니다. 그리고 수정하지 않고 중단해야합니다. cron을 참고하세요.
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b3b8b495-e866-48b0-b107-599e30e0bd12/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-01-29_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.30.26.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220129%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220129T035913Z&X-Amz-Expires=86400&X-Amz-Signature=78d8b6066888184009c4414724ead96c6b7df59595fba5cbd4d8bee25e33f7ee&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-01-29%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252012.30.26.png%22&x-id=GetObject)
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bd54f7dd-ba36-43fc-a348-62c40663d106/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-01-29_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.30.52.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220129%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220129T035957Z&X-Amz-Expires=86400&X-Amz-Signature=a1b1e9703e9cbb009dde23e7dfc6887292c04c0709b00be3f72287816ae7dae8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-01-29%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252012.30.52.png%22&x-id=GetObject)
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/61d846c9-5ad7-4b6e-8cb8-7f4dd25f5c5d/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-01-29_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.31.06.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220129%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220129T040011Z&X-Amz-Expires=86400&X-Amz-Signature=eb21181b2e8298b8579ecb8717b19065d7b87fb18fe246d2438d28e05d4d46bb&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-01-29%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252012.31.06.png%22&x-id=GetObject)

---

- 서브젝트를 읽어도 관련단어를 아예모르니간 어떻게 접근해야할지 아직 모르겠다.
- 먼저 Virtualbox or UTM에 대해서 알아보고, 모르는 단어부터 천천히
  알아가는것이 먼저일듯 싶다.
