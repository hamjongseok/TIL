# **🌎Born2beroot🌎**

## **sudo**

- Super User Do의 줄임말
- UNIX에서는 root계정만이 모든 명령을 실행, 특정한 중요작업을 수행할수있다.
- sudo명령어를 통해 다른 일반 사용자가 일부 명령을 실행하고 시스템 작업을 수행할 수 있도록 허용해준다.

---

```c
sudo 관련 명령어

dpkg -l sudo (설치여부 확인)

apt install sudo (수도설치)

su - (root계정으로 이동)

sudo (명령어)
일반유저가 root권한으로 명령어 실행

su (계정명)
현재 유저를 로그아웃 하지않은 채로 다른 사용자 계정으로 전환

visudo (sudoer파일 접근)

```

---

### subject 항목

- 비밀번호 오류는 3번으로 제한됩니다. ⭕️

  - `passwd_tries=3`

- sudo를 사용할 때, 잘못 된 암호로 인한 오류가 발생할 경우 커스텀 메시지를 표시합니다. ⭕️

  - `badpass_message=""`
  - Defaults authfail_message="원하는 에러메세지" #권한 획득 실패 시 출력 (sudo 인증 실패 시,3번의 비번 틀릴경우)

- sudo를 사용할 때의 모든 입출력 동작은 기록되어야 합니다. 로그 파일은 `/var/log/sudo/` 폴더에 저장됩니다. ⭕️
  - `iolog_dir="/var/log/sudo/"` (로그 저장할 경로)
- sudo를 이용한 action들은 input 과 output이 archived(모여있어야함)⭕️

  - Defalt log_input : sudo를 통해 입력된 input은 로그에 기록된다.
  - Defalt log_output : sudo를 통해 입력된 output은 로그에 기록된다

  ```c
  log 파일이란 ?
  - 컴퓨터의 모든 사용내역을 기록하고 있는 파일을 말한다.
  - 해킹 등의 사건이 발생했을때, 로그파일을 분석하여 사건의 원인을 파악한다.
  ```

- 보안 문제 관련해서, TTY 모드를 활성화합니다.⭕️
  - `requiretty` (tty환경에서만 sudo 명령이 실행될 수 있도록 한다.)

```c
  TTY (Teletypewriter)

  콘솔의 한 종류로 Ctrl-Alt-F1 ~ F6 키조합으로 사용할수있는 OS 에서 제공하는 가상콘솔 이다. 실제 물리적인 장치가 연결된것이 아니기 때문에 커널에서 터미널을 emulation 한다. TTY화면간 이동은 ALT+F1~F6이며 GUI환경 복귀는 ALT+F7이다.

출처: https://booolean.tistory.com/666 [Boolean]

콘솔이란 ?
CLI 혹은 CUI라고 불리며 컴퓨터를 운용하기 위한 목적으로 테스트를 사용자와 주고 받는 방식의 인터페이스를 말한다.

```

- 보안 문제 관련해서, sudo에서 사용할 수 있는 경로는 제한됩니다. ⭕️
  - `secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"`

```c
  sudo명령 실행 시 현재 계정의 쉘이 아닌 새로운 쉘을 생성하고 그 안에서 명령을 실행하는데, 이 때 명령을 찾을 경로를 나열한 환경변수인 PATH값이 secure_path

  shell 명령어들은 PATH 환경변수에 지정된 경로에서 바이너리 파일을 찾는다.

 sudo 권한이 있는 사용자의 PATH 환경변수에 악성코드로 인한 경로가 포함되어 있어 특정 명령 실행시 해당 경로에서 악성 파일이 실행될 경우 유저가 sudo를 통해 시스템 전반에 대한 권한을 부여받은 채 해당 명령을 실행한다면 시스템에 큰 문제가 생길 것이다.

이러한 상황을 방지하기 위해 sudo 가 실행되는 가상 쉘에서 명령어의 바이너리 파일 경로를 secure_path 로 제한하는 것이다.
```

---

## Group

- 이 사용자는 user42 와 sudo 그룹에 속해야 합니다 ⭕️
  - groupadd user42 명령어를 통해 user42그룹 추가
  - usermod -aG sudo,user42 <사용자이름> 명령어를 통해 해당 그룹에 유저를 추가

```c
G 옵션:
G옵션만 붙힌 상태에서 그룹 설정 시, 명령어에 나열된 그룹만 추가가 되며 명령어에 나열되어 있지 않지만 유저가 속해있는 그룹은 전부 탈퇴된다.

a 옵션:
G옵션에서만 함께 쓰일 수 있고, G옵션만 붙었을 때와 달리, 유저가 속해있지만 명령어에 나열되어있지 않는 그룹에 관하여 탈퇴처리 되지 않는다.

"sudo deluser 사용자명 그룹명"을 통해 그룹에서 사용자를 제거할 수 있다.

"sudo userdel -r 사용자명" 통해 사용자 제거 가능.
```

- id jham (어느 그룹에 속해있는지 나온다.)

---

## `UFW`

- 방화벽이란 ?
  - 외부 사용자(WAN)들이 내부 네트워크(LAN)에 접근하지 못하도록 하는 일종의 내부 네트워크 방어도구이다.
  - 방화벽은 신뢰할 수 있는 내부 네트워크, 신뢰할 수 없는 외부 네트워크 간의 장벽을 구성한다.
  - 서로 다른 네트워크를 지나는 데이터를 허용 또는 거부 하거나 검열 또는 수정하는 하드웨어 또는 소프트웨어다.
- UFW ?
  - Uncomplicated Firewall의 약자
  - Debian 계열 및 다양한 리눅스 환경에서 작동되는 사용하기 쉬운 방화벽 관리 프로그램
  - UTF는 손쉬운 조작으로 iptable 및 사슬 설정을 대신해준다.(Uncomplicated: 복잡하지 않은) 데비안의 기본 방화벽은 iptable이다.
  - iptable이란?
    - 시스템관리자가 리눅스 커널 방화벽이 제공하는 테이블과 그것들을 저장하는 체인, 규칙들을 구성할 수 있게 해주는 사용자 공간 응용프로그램

```
평가때 사용하는 명령어

ufw enable: 방화벽 활성화

ufw status: 방화벽 상태를 확인

ufw delete (규칙 번호): 정의된 특정 번호의 규칙 제거

ufw allow (포트넘버): 특정 포트넘버 접속 허용

ufw deny (포트넘버): 특정 포트넘버 접속 제한
```

---

## SSH

- Secure Shell Protocol
- 원격 호스트에 접속하기 위해 사용되는 보안 프로토콜
- 대표적인 사용

  - 데이터 전송 (깃 푸시)
  - 원격제어 (aws같은 클라우드 서비스)
  - 포트포워딩

- apt search openssh-server 명령어를 통해 openssh가 깔려있는지 확인.
  - 깔려있지 않다면, apt install open ssh-server 명령어로 설치
- 깔려있지 않다면, apt install open ssh-server 명령어로 설치
- sudo vim /etc/ssh/sshd_config 명령어를 통해 ssh설정을 변경
- PermitRootLogin 부분을 no로 바꾼다. 해당 옵션을 통해 외부에서 root로 로그인하는 것을 막을 수 있다.
- hostname -I
  - 가상 ip 확인
- 포트포워딩
  - ssh -p 4242 jham@192.168.56.1

---

## 비밀번호 정책

chage -l <사용자>를 통해 현재 사용자의 암호정보를 알 수 있다.

기본 정책

- Last password change (-d) : 마지막 패스워드 변경일
- Password expires : 암호 만료일
- Password inactive(-I (대문자i)) : 비활성화 유예기간
- Account expires(-E) : 계정 만료일
- Minimum number .... (-m) : 패스워드 변경 후 최소 사용 기간, 즉 최소 의무 사용일
- Maximum number .... (-M) : 패스워드 변경 후 변경 없이 사용가능한 최대 일 수
- Number of days of warning ... (-W) : 패스워드 만료 전 경고메세지를 보낼 일 수

- 서브젝트에서 요구사항

1. password 는 30일마다 만료되어야한다. -M 30
2. 비밀번호 최소 사용일이 2일 이다 (비밀번호 변경후 2일이 지나야 다시변경 가능) -m 2
3. 유저는 비밀번호 만료 7일전에 경고 메세지를 받아야 한다. -W 7

- sudo chage -M 30 -m 2 -W 7 jham 으로 설정 완료

전체 정책 변경

- 위 방법은 나의 계정만 정책을 변경시키고 이제 새로 만들어질 user에도 같은 정책이 적용되는 전체 정책을 변경해야한다.
- vi /etc/pam.d/common-password 를 통해 현재 패스워드 정책을 확인할 수 있다.
- 패스워드 정책 설정을 위한 모듈을 설치
- sudo apt install libpam-cracklib

```
비밀번호는 최소 10자리여야 한다. minlen=10

영어 대문자 + 숫자는 꼭 포함하고 있어야 한다. ucredit숫자, decredit숫자

3개 이상의 연속된 동일한 문자를 가지면 안된다. maxrepeat = 3

비밀번호는 사용자의 이름을 포함하면 안된다. reject_username

비밀번호는 이전의 비밀번호와 다른 최소 7글자를 가져야 한다. difok = 7

root password는 이 정책을 따라야한다. enforce_for_root

```

- `retry=N` : 암호입력을 N회로 설정
- `minlen=N` : 암호의 최소 길이는 N
- `difok=N` : 기존 패스워드와 달라야하는 문자 수 N
- `ucredit=-N` : 대문자 N개 이상
- `lcredit=-N` : 소문자 N개 이상 -1
- `decredit=-N` : 숫자 N개 이상 -1

(N < 0)
새 패스워드에 있어야 하는 대문자 최소 개수.

- `reject_username` : 사용자의 이름이 그대로 혹은 뒤집혀 패스워드에 있는지 검사
- `enforce_for_root` : root사용자가 패스워드를 바꾸려 할 때에도 위 조건 적용
- `maxrepeat=N` : 같은 문자가 N번 이상 연속해서 나오는지 검사

---

## hostname

- hostnamectl 명령어를 통해 hostname을 확인할 수 있다.
- sudo vi /etc/hostname 들어가서 바꿈, 껏다가 켜야함

## LVM

- lsblk 명령어로 파티션을 확인 할 수 있다.
- mandatory 파트 예시와 비교

LVM이란 ?

- Logical Volume Manager
- 이름 뜻 그대로 Logical(논리적인) Volume(공간을) Manager(만들고 관리 해주는 프로그램이다.
- 디스크 효율 관리 기술
- 사용 이유
  - 여러개의 디스크 공간을 합쳐서 하나인 양 사용하기 위해
  - 사용하기 애매한 공간의 디스크 파티션들을 활용하기 위해
  - 기존에 사용중인 디스크의 공간을 확장할 수 있기 때문에
- 파티션이란?
  - 어떤 하나의 무언가를 여러개로 나누는 개념
- LVM ?
  - 여러 디스크 공간, 짜투리 공간을 합쳐서 하나로 만드는 것
  - 한번 파티션을 나누면 서로 용량을 주고 받을 수 없다.
  - 파티션을 논리적인 개념(LVM)으로 나누면, 용량을 서로 주고 받을 수 있다.
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/e2d603f4-b7a7-450d-a9fa-0f0e4f7fa152/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.13.22.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220314%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220314T041338Z&X-Amz-Expires=86400&X-Amz-Signature=0b8ecf4a32eb7f987849821cce3320595b9c353ff467e323d5d658288ee7ae07&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.13.22.png%22&x-id=GetObject)

## LVM 용어

- PV(Physical Volume)

  - LVM에서 블록 장치를 사용하려면 PV로 초기화를 해야한다. 즉, 파티션들을 LVM에서 사용할 수 있게 변환하는것
  - PV는 일정한 크기의 PE(Pysyical Extent)들로 구성이 된다.

- PE((Physical Extent)
  - PV를 구성하는 일정한 크기의 블록으로 기본크기는 4MB
  - V(Logical Volume)의 LE(Logical Extent)들과 1:1로 맵핑된다. 그렇기에 항상 PE와 LE의 크기는 동일하다.
- PV로 초기화시킨 모습
  ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/988c7566-0423-4c93-9f6c-009db483b376/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.29.13.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220314%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220314T042925Z&X-Amz-Expires=86400&X-Amz-Signature=3b5156c1f6c8f30eed755597be8014cf45514207ccaa52aa68099e179bc87601&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.29.13.png%22&x-id=GetObject)
- VG(Volume Group)
  - PV들의 집합으로 LV를 할당할 수 있는 공간이다
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/5640f21b-ea32-4204-8d28-510a675a82f8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.30.29.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220314%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220314T043103Z&X-Amz-Expires=86400&X-Amz-Signature=02a3d0ca3602378f7d0f0c1ad4336d799d2bf0ea6eca45eab4540a51235e0119&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.30.29.png%22&x-id=GetObject)
- LV(Logical Volume)
  - 사용자가 최종적으로 다루게되는 논리적인 스토리지
- LE(Logical Extent)
  - LV를 구성하는 일정한 크기의 블록으로 기본크기는 4MB이다.
  - 항상 PE와 LE의 크기는 동일하다.
    ![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/cb92bdfe-e3f1-43a5-8e89-ac7ab4ac21ee/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_1.32.24.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220314%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220314T043318Z&X-Amz-Expires=86400&X-Amz-Signature=161f90c2d089e49b5fb7f14c034a86b2845a95cc36a73af52a50055ae4e53f29&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-03-14%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%25201.32.24.png%22&x-id=GetObject)
  - VG에서 필요에 따라 LV를 만들어서 사용한다.

---

### cron

- 특정한 시간에 or 특정 시간마다 어떤 작업을 자동으로 수행하게 하는 명령어

crontab

- cron작업을 설정하는 파일
- cron프로세스는 /etc/crontab 파일에 설정된 것을 읽어 작업을 수행
- sudo cat /etc/crontab

cron 설정 방법

- sudo crontab -e
- \*/10 \* \* \* \* /monitoring.sh | wall : 10분마다 root권한에서 "/monitoring.sh | wall" 실행
- \* \* \* \* sleep [ ]; command : 초단위로 컨트로 하려면
- \* \* \* \* \* 명령어 & sleep 30; 명령어

## monitoring.sh

- OS의 architecture 및 kernel version
  - printf "#Architecture: "
  - uname -srvmo
    - -s는 커널 이름, -r은 커널릴리즈, -v는 커널 버전, -m은 아키텍쳐, -o는 os출력
- physical(물리적) processors 개수
  - printf "#CPU physical : "
  - nproc --all
    - "nproc --all"을 통해 설치된 프로세서의 갯수를 출력
- virtual(가상) processors 개수
  - printf "#vCPU : "
  - cat /proc/cpuinfo | grep processor | wc -l
    - 가상 프로세서(vCPU)의 갯수를 출력
    - wc -l : 라인수 보여줌
    - grep : 텍스트 파일에서 원하는 문자열이 들어간 행을 찾아 출력하는 명령어.
- 서버에서 사용 가능한 RAM 및 사용률(%)

  - printf "#Memory Usage: "
  - free -m | grep Mem | awk '{printf"%d/%dMB (%.2f%%)\n", $3, $2, $3/$2 \* 100}'
    - // free 사용가능한 메모리확인
    - free명령어는 리눅스 시스템에서 메모리의 전체적인 현황을 살펴볼 수 있는 명령어
    - -m 옵션을 통해 MB로 단위 변경
    - awk를 사용하여 적절한 값 도출

- 서버에서 사용 가능한 메모리 및 사용률(%)
  - printf "#Disk Usage: "
  - df -BM -a | grep /dev/mapper/ | awk '{sum+=$3}END{print sum}' | tr -d '\n'
    - df 사용가능한 디스크 용량 확인
    - -BM , MB로 변경(-m 도 가능 ) -a , 모두(0인것도 보기)
    - '{sum+=$3}END{print sum}' 세번째 필드의 합계산
    - tr -d '\n' 개행 삭제
  - printf "/"
  - df -BM -a | grep /dev/mapper/ | awk '{sum+=$4}END{print sum}' | tr -d '\n'
  - printf "MB ("
  - df -BM -a | grep /dev/mapper/ | awk '{sum1+=$3 ; sum2+=$4}END{printf "%d", sum1 / sum2 \* 100}' | tr -d '\n'
  - printf "%%)\n"
- Cpu 사용량

  - printf "#CPU load: "
  - mpstat | grep all | awk '{printf "%.2f%%\n", 100-$13}'
    - sysstat를 다운받아 mpstat 명령어를 사용하면 쉽게 현재 CPU의 사용량을 알 수 있다.
    - mpstat 명령어에서 마지막 컬럼을 활용하여 결과를 도출

- 마지막 부팅날짜 및 시간
  - who -b | sed 's/^ \*system boot //g'
    - last reboot 명령어를 사용하면 마지막으로 재기동한 시간이 언제인지 정렬하여 출력한다.
    - who 명령어는 현재 내가 어떤 사용자로 접속을 했는지 확인하기 위해 사용할 수 있다.
    - -b 옵션을 사용하면 마지막 시스템 부팅 시간을 출력한다는 뜻.
    - sed도 추출하는 명령어
- LVM이 활성 상태인지 여부
  - printf "#LVM use: "
  - if [ "$(lsblk | grep lvm | wc -l)" -gt 0 ] ; then printf "yes\n" ; else printf "no\n" ; fi
    - lsblk 명령어를 사용하면 현재 장착된 디스크의 주요 사양을 확인할 수 있다.
    - 리눅스 if문 활용
- 활성 연결 수

  - printf "#Connections TCP : "
  - ss | grep -i tcp | wc -l | tr -d '\n'
  - 통신하는 소켓 , 원격하면 1 생긴다.

- 사용자 정보 확인
  - printf "#User log: "
    - who | wc -l
- mac주소 확인

  - printf "#Network: IP "
  - hostname -I | tr -d '\n'
    - ip adress 확인;
  - printf " ("
  - ip link show | awk '$1 == "link/ether" {print $2}' | tr -d '\n'
    - //모든 네트워크 인터페이스의 상태를 관리하고 출력함
  - printf ")\n"

- sudo 프로그램 실행된 명령 수

  - printf "#Sudo : "
  - journalctl \_COMM=sudo | grep COMMAND | wc -l | tr -d '\n'

    - journalctl을 사용하면 systemd-journald 데몬이 수집한 모든 로그 정보를 볼 수 있다.
    - journalctl을 사용하여 특정 로그를 보고싶다면 \_COMM=<특정> 옵션을 추가하면 된다.

  - printf " cmd\n"

- 본투비 루트 끝 4월 20일까지 push_swap 어느정도 구현 끝내고 말까지 평가 진행 목표
