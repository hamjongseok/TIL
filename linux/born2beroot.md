# **🌎Born2beroot🌎**

## **Subject**

---

- This project aims to introduce you to the wonderful world of virtualization.

## General guidelines

---

- ~~Virtualbox or UTM 사용 가능
  (virtualbox 사용)~~
- ~~서버 셋업하기. CUI로 미니멈한 서버를 세팅~~
- ~~설치는 최소한으로 진행되어야 한다.(GUI 설치 금지!)~~
- ~~OS로는 Debian의 최신 stable 버전이나 CentOS의 최신 stable 중 하나를 선택해라. (Debian)~~
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
- ~~가상 머신의 `hostname`은 `[당신의 로그인]42` 형식이어야 합니다. 예시: `wil42`~~
- 강한 암호 폴리시를 구현해야합니다.
- ~~엄격한 규칙에 따라 `sudo`를 설치하고 구성해야 합니다.~~
- root 유저 외에도 `[당신의 로그인]`이 유저네임인 유저가 존재해야 합니다.
- ~~이 사용자는 `user42` 와 `sudo` 그룹에 속해야 합니다~~
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

---

# 평가표

Introduction
Please comply with the following rules:

- Remain polite, courteous, respectful and constructive throughout the
  evaluation process. The well-being of the community depends on it.

- Identify with the student or group whose work is evaluated the possible
  dysfunctions in their project. Take the time to discuss and debate the
  problems that may have been identified.

- You must consider that there might be some differences in how your peers
  might have understood the project's instructions and the scope of its
  functionalities. Always keep an open mind and grade them as honestly as
  possible. The pedagogy is useful only and only if the peer-evaluation is
  done seriously.

Guidelines

- Only grade the work that was turned in the Git repository of the evaluated
  student or group.

- Double-check that the Git repository belongs to the student(s). Ensure that
  the project is the one expected. Also, check that "git clone" is used in an
  empty folder.

- Check carefully that no malicious aliases was used to fool you and make you
  evaluate something that is not the content of the official repository.

- To avoid any surprises and if applicable, review together any scripts used
  to facilitate the grading (scripts for testing or automation).

- If you have not completed the assignment you are going to evaluate, you have
  to read the entire subject prior to starting the evaluation process.

- Use the available flags to report an empty repository, a non-functioning
  program, a Norm error, cheating, and so forth.
  In these cases, the evaluation process ends and the final grade is 0,
  or -42 in case of cheating. However, except for cheating, student are
  strongly encouraged to review together the work that was turned in, in order
  to identify any mistakes that shouldn't be repeated in the future.

Preliminaries 사전준비

- If cheating is suspected, the evaluation stops here. Use the "Cheat" flag to report it. Take this decision calmly, wisely, and please, use this button with caution.

Preliminary tests

- Defense can only happen if the student being evaluated or group is present.
  This way everybody learns by sharing knowledge with each other.
- If no work has been submitted (or wrong files, wrong directory, or
  wrong filenames), the grade is 0, and the evaluation process ends.
- For this project, you have to clone their Git repository on their
  station.

General instructions

- During the defense, as soon as you need help to verify a point, the student
  evaluated must help you.
- Ensure that the "signature.txt" file is present at the root of the cloned repository.

  - 복제된 리포지토리의 루트에 "signature.txt" 파일이 있는지 확인합니다.

- Check that the signature contained in "signature.txt" is identical
  to that of the ".vdi" file of the virtual machine to be evaluated. A simple
  "diff" should allow you to compare the two signatures. If necessary, ask the
  student being evaluated where their ".vdi" file is located.
  - "signature.txt"에 포함된 서명이 평가할 가상 시스템의 ".vdi" 파일의 서명과 동일한지 확인합니다. 단순한 「diff」를 사용하면, 2개의 시그니처를 비교할 수 있습니다. 필요에 따라서, 평가 대상의 학생에게 「.vdi」파일의 위치를 묻습니다.
- As a precaution, you can duplicate the initial virtual machine in order
  to keep a copy.
- Start the virtual machine to be evaluated.
- If something doesn't work as expected or the two signatures differ,
  the evaluation stops here.

Mandatory part
The project consists of creating and configuring a virtual machine following strict rules. The student being evaluated will have to help you during the defense. Make sure that all of the following points are observed.

signature.txt에 포함된 서명이 평가할 가상 시스템의 ".vdi" 파일의 서명과 동일한지 확인합니다.
간단한 "diff"로 두 서명을 비교할 수 있습니다. 필요한 경우 평가 중인 학생에게
".vdi" 파일이 어디에 있는지 묻습니다.

Project overview

- The student being evaluated should explain to you simply:
- 간단히 설명할수있어야한다.
- How a virtual machine works.
- 어떻게 가상머신이 작동하는지 ?
- Their choice of operating system.
- 선택한 운영 체제.
- The basic differences between CentOS and Debian.
- CentOS와 데비안의 기본적인 차이점.
- The purpose of virtual machines.
- 가상 시스템의 용도
- If the evaluated student chose CentOS: what SELinux and DNF are.
- If the evaluated student chose Debian: the difference between
  aptitude and apt, and what APPArmor is.
  - 만약 평가된 학생이 데비안: Apparmor과 apt의 차이, 그리고 APPArmor가 무엇인지 ?
- During the defense, a script must display information all
  every 10 minutes. Its operation will be checked in detail later.
  If the explanations are not clear, the evaluation stops here.
- 스크립트에 정보가 모두 표시되어야 합니다. 10분마다

---

Simple setup

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Ensure that the machine does not have a graphical environment at launch.
- gui가 설치안되어있는지 확인
- A password will be requested before attempting to connect to this machine.

  - 이 컴퓨터에 연결을 시도하기 전에 암호가 필요합니다.

  Finally, connect with a user with the help of the student being evaluated.
  This user must not be root.

  Pay attention to the password chosen, it must follow the rules imposed in the subject.

- Check that the UFW service is started with the help of the evaluator.
- Check that the SSH service is started with the help of the evaluator.
- Check that the chosen operating system is Debian or CentOS with the help of the evaluator.
  If something does not work as expected or is not clearly explained,
  the evaluation stops here.

---

User

Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

The subject requests that a user with the login of the student being evaluated is present
on the virtual machine. Check that it has been added and that it belongs to the
"sudo" and "user42" groups.

- user jham이 있는지 확인하고 그것들이 sudo와 user42에 속해있는지 확인

Make sure the rules imposed in the subject concerning the password policy have been put in place by
following the following steps.

- 암호규칙이 제대로 되어있는지 확인

First, create a new user. Assign it a password of your choice, respecting the subject rules. The
student being evaluated must now explain to you how they were able to set up the rules requested
in the subject on their virtual machine.
Normally there should be one or two modified files. If there is any problem, the evaluation stops here.

- Now that you have a new user, ask the student being evaluated to create a group named "evaluating" in
  front of you and assign it to this user. Finally, check that this user belongs to the "evaluating" group.
- 이제 새 사용자가 생겼으니 평가 대상 학생에게 앞에 "evaluating"이라는 그룹을 만들어
  이 사용자에게 할당하도록 요청합니다. 마지막으로 이 사용자가 "evaluating" 그룹에 속하는지 확인합니다.

- Finally, ask the student being evaluated to explain the advantages of this password policy, as well as the
  advantages and disadvantages of its implementation. Of course, answering that it is because the subject asks
  for it does not count.
- 마지막으로, 평가 대상 학생에게 비밀번호 정책의 장점과 구현의 장점을 설명하도록 요청합니다.
  물론 주체가 요구하기 때문이라고 대답하는 것은 중요하지 않다.
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

Hostname and partitions

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Check that the hostname of the machine is correctly formatted as follows: login42 (login of the student being evaluated).
- host이름이 42인지
- Modify this hostname by replacing the login with yours, then restart the machine. If on restart, the hostname has not been updated, the evaluation stops here.
- 호스트이름을 바꾸고 (아무거나 바꾸라는건지 ?) 다시 시작했을때 호스트이름이 바뀌어야한다.

- You can now restore the machine to the original hostname.
- 이제 시스템을 원래 호스트 이름으로 복원할수있다
- Ask the student being evaluated how to view the partitions for this virtual machine.
- Compare the output with the example given in the subject. Please note: if the
  student evaluated makes the bonuses, it will be necessary to refer to the bonus example.
- 파티션 보여주고 서브젝트와 비교

- This part is an opportunity to discuss the scores! The student being evaluated should
  give you a brief explanation of how LVM works and what it is all about.
- Lvm에 대한 설명, 동작원리
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

SUDO

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Check that the "sudo" program is properly installed on the virtual machine.
- sudo 설치되어있는지 확인
- The student being evaluated should now show assigning your new user to the "sudo" group.
- 새사용자를 sudo그룹에 할당 시키는것을 보여줘라
- The subject imposes strict rules for sudo. The student being evaluated must first explain the value and operation of sudo using examples of their choice.
  In a second step, it must show you the implementation of the rules imposed by the subject.
- sudo 규칙에 대해서 설명
- Verify that the "/var/log/sudo/" folder exists and has at least one file. Check the contents of the files in this folder, You should see a history of the commands used with sudo.
- "/var/log/sudo/" 폴더가 있고 파일이 하나 이상 있는지 확인합니다. 이 폴더의 파일 내용을 확인하십시오. sudo에 사용된 명령어의 기록이 표시됩니다.
- Finally, try to run a command via sudo. See if the file (s) in the "/var/log/sudo/" folder have been updated.
- sudo 명령을 실행해서 파일이 업데이트가 되는지 확인 시켜줘라
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

UFW

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Check that the "UFW" program is properly installed on the virtual machine.
- UFW가 설치되어 있는지 확인
- Check that it is working properly.
- 정상적으로 작동 되는지 확인
- The student being evaluated should explain to you basically what UFW is and the value of using it.
- 평가 대상 학생은 기본적으로 UFW가 무엇인지, 그리고 UFW를 사용하는 가치에 대해 설명해야 합니다.
- List the active rules in UFW. A rule must exist for port 4242.
- UFW 활성규칙을 나열 ?, 포트 4242가 있어야한다. 라는거지 ?
- Add a new rule to open port 8080. Check that this one has been added by listing the active rules.
- 8080포트를 추가해서 확인 시켜라
- Finally, delete this new rule with the help of the student being evaluated.
- 평가중인 학생의 도움을 받아서 이 규칙을 삭제해라 ?
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

SSH

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Check that the SSH service is properly installed on the virtual machine.
- ssh가 제대로 설치되어있는지 확인
- Check that it is working properly.
- 정상적으로 작동하는지 확인
- The student being evaluated must be able to explain to you basically what SSH is and the value of using it.
- SSH가 무엇이고 SSH를 사용하는 가치를 기본적으로 설명할 수 있어야 합니다.
- Verify that the SSH service only uses port 4242.
- SSH 서비스가 포트 4242만 사용하는지 확인합니다.
- The student being evaluated should help you use SSH in order to log in with the newly created user.
- 평가 중인 학생은 SSH를 사용하여 새로 만든 사용자로 로그인하는 데 도움이 됩니다.
- To do this, you can use a key or a simple password. It will depend on the student being evaluated.
- 이렇게 하려면 키나 간단한 암호를 사용하면 됩니다. 그것은 평가받는 학생에 따라 달라질 것입니다.
- Of course, you have to make sure that you cannot use SSH with the "root" user as stated in the subject.
- 물론 제목에 명시된 "루트" 사용자와 SSH를 함께 사용할 수 없도록 해야 합니다.
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

Script monitoring

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

The student being evaluated should explain to you simply:

- 간단하게 설명해야한다.
- How their script works by showing you the code.
- 코드를 보여줌으로써 그들의 스크립트가 작동하는 방식.
- What "cron" is.
- cron이 어떤것인지 ?
- How the student being evaluated set up their script so that it runs every 10 minutes from when the server starts.
- 평가 중인 학생이 서버가 시작될 때부터 10분마다 실행되도록 스크립트를 설정하는 방법입니다.
- Once the correct functioning of the script has been verified, the student being evaluated should ensure that this script runs every minute.
- 매분 마다 실행이 잘되는지 확인해 볼것
- You can run whatever you want to make sure the script runs with dynamic values correctly.
- Finally, the student being evaluated should make the script stop running when the server has started up, but without modifying the script itself.
- 마지막으로 평가 중인 학생은 서버가 시작될 때 스크립트 자체를 수정하지 않고 스크립트 실행을 중지해야 합니다.
- To check this point, you will have to restart the server one last time. At startup, it will be necessary to check that the script still exists in the same place, that its rights have remained unchanged, and that it has not been modified.
- 이 점을 확인하려면 서버를 마지막으로 재시작해야 합니다. 시작할 때 스크립트가 여전히 같은 장소에 존재하는지, 스크립트의 권한이 변경되지 않았는지, 수정되지 않았는지 확인해야 합니다.
- If something does not work as expected or is not clearly explained, the evaluation stops here.

본투비 평가 끝
