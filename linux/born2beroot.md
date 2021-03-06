# **๐Born2beroot๐**

## **Subject**

---

- This project aims to introduce you to the wonderful world of virtualization.

## General guidelines

---

- ~~Virtualbox or UTM ์ฌ์ฉ ๊ฐ๋ฅ
  (virtualbox ์ฌ์ฉ)~~
- ~~์๋ฒ ์์ํ๊ธฐ. CUI๋ก ๋ฏธ๋๋ฉํ ์๋ฒ๋ฅผ ์ธํ~~
- ~~์ค์น๋ ์ต์ํ์ผ๋ก ์งํ๋์ด์ผ ํ๋ค.(GUI ์ค์น ๊ธ์ง!)~~
- ~~OS๋ก๋ Debian์ ์ต์  stable ๋ฒ์ ์ด๋ CentOS์ ์ต์  stable ์ค ํ๋๋ฅผ ์ ํํด๋ผ. (Debian)~~
- CentOS ์์ kdump ์์์ ํ์ํ์ง ์๋ค. SElinux๋ ํ์ AppArmor for Debian๋ ํ์
- LVM๋ฅผ ์ฌ์ฉํด์ ์ํธํ๋ ํํฐ์์ 2๊ฐ ์ด์ ์์ฑํด์ผ ํ๋ค.

---

![image description](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0b0587b6-306b-4f41-99c6-e61a69423256/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-01-29_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12.05.02.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220129%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220129T034741Z&X-Amz-Expires=86400&X-Amz-Signature=8a62458682a19d2d563c8dbc888c4909c26a5d1c8c94ceddf9715931628b8c10&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-01-29%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252012.05.02.png%22&x-id=GetObject)

---

- aptitude์ apt ์ ์ฐจ์ด, SELinux ํน์ AppArmor์ด ๋ฌด์์ธ์ง ์๊ณ  ์์ด์ผ ํ๋ค.
- ์ฌ์ฉํ๋ ์ด์์ฒด์ ์ ๋ํ ์ค๋ช
- SSH ์๋น์ค๋ 4242 ํฌํธ์์๋ง ์คํ๋๋ค. ๋ณด์์์ ์ด์ ๋ก SSH๋ฅผ root๋ก ์ฌ์ฉํด์ ์ฐ๊ฒฐํ๋ ๊ฒ์ ๊ธ์ง๋ค๋ค.
- ssh๊ฐ ์ด๋ป๊ฒ ์๋ํ๋์ง ์๊ณ  ์์ด์ผ ํ๋ค.
- UFW ๋ฐฉํ๋ฒฝ์ ์ด์ฉํด์ผํ๊ณ  4242ํฌํธ๋ง ์ด์ด๋์ผํ๋ค.
- ๋ฐฉํ๋ฒฝ์ ๊ฐ์๋จธ์ ์ ์์ํ ๋ ์๋ํด์ผํ๋ค. centOS์์ ๊ธฐ๋ณธ๋ฐฉํ๋ฒฝ ๋์ ์ UFW๋ฐฉํ๋ฒฝ์ ์ด์ฉํด์ผ ํ๋ค. ์ค์นํ๊ธฐ ์ํด์๋ DNF๊ฐ ํ์ํ ๋ฏ
- ~~๊ฐ์ ๋จธ์ ์ย `hostname`์ย `[๋น์ ์ ๋ก๊ทธ์ธ]42`ย ํ์์ด์ด์ผ ํฉ๋๋ค. ์์:ย `wil42`~~
- ๊ฐํ ์ํธ ํด๋ฆฌ์๋ฅผ ๊ตฌํํด์ผํฉ๋๋ค.
- ~~์๊ฒฉํ ๊ท์น์ ๋ฐ๋ผย `sudo`๋ฅผ ์ค์นํ๊ณ  ๊ตฌ์ฑํด์ผ ํฉ๋๋ค.~~
- root ์ ์  ์ธ์๋ย `[๋น์ ์ ๋ก๊ทธ์ธ]`์ด ์ ์ ๋ค์์ธ ์ ์ ๊ฐ ์กด์ฌํด์ผ ํฉ๋๋ค.
- ~~์ด ์ฌ์ฉ์๋ย `user42`ย ์ย `sudo`ย ๊ทธ๋ฃน์ ์ํด์ผ ํฉ๋๋ค~~
- ํ๊ฐ ์ค์ ์ ์ ์ ๋ฅผ ์์ฑํด์ ๊ทธ๋ฃน์ ํ ๋นํด์ผ ํฉ๋๋ค.

- ๊ฐํ ์ํธ๋ฅผ ์์ํ๊ธฐ ์ํด, ๋ค์ ์๊ตฌ ์ฌํญ์ ์ค์ํด์ผ ํฉ๋๋ค.

```c
1. password ๋ 30์ผ๋ง๋ค ๋ง๋ฃ๋์ด์ผํ๋ค.
2. ๋น๋ฐ๋ฒํธ ์ต์ ์ฌ์ฉ์ผ์ด 2์ผ ์ด๋ค (๋น๋ฐ๋ฒํธ ๋ณ๊ฒฝํ 2์ผ์ด ์ง๋์ผ ๋ค์๋ณ๊ฒฝ ๊ฐ๋ฅ)
3. ์ ์ ๋ ๋น๋ฐ๋ฒํธ ๋ง๋ฃ 7์ผ์ ์ ๊ฒฝ๊ณ  ๋ฉ์ธ์ง๋ฅผ ๋ฐ์์ผ ํ๋ค.
4. ๋น๋ฐ๋ฒํธ๋ ์ต์ 10์๋ฆฌ์ฌ์ผ ํ๋ค. ์์ด ๋๋ฌธ์ + ์ซ์๋ ๊ผญ ํฌํจํ๊ณ  ์์ด์ผ ํ๋ค. 3๊ฐ ์ด์์ ์ฐ์๋ ๋์ผํ ๋ฌธ์๋ฅผ ๊ฐ์ง๋ฉด ์๋๋ค.
5. ๋น๋ฐ๋ฒํธ๋ ์ฌ์ฉ์์ ์ด๋ฆ์ ํฌํจํ๋ฉด ์๋๋ค.
6. ๋น๋ฐ๋ฒํธ๋ ์ด์ ์ ๋น๋ฐ๋ฒํธ์ ๋ค๋ฅธ ์ต์ 7๊ธ์๋ฅผ ๊ฐ์ ธ์ผ ํ๋ค.
7. ๋น์ฐํ root password๋ ์ด ์ ์ฑ์ ๋ฐ๋ผ์ผํ๋ค.
8. ๊ตฌ์ฑ file์ ์ํํ ํ, ๊ฐ์๋จธ์ ์ ์กด์ฌํ๋ ๋ชจ๋  ๊ณ์ ์ ๋น๋ฐ๋ฒํธ๋ฅผ ๋ฐ๊ฟ์ผ ํ๋ค. ๋ฃจํธ๊ณ์  ํฌํจ.
```

---

- Sudo ๊ทธ๋ฃน์ ๋ค์์ ์๊ตฌ๋๋ ๊ฐ๋ ฅํ ๊ตฌ์ฑ์ ์ค์ํด์ผ ํฉ๋๋ค

```c
1. sudo๋ฅผ ์ด์ฉํ ์ธ์ฆ์ 3๋ฒ์ ์๋๋ก ์ ํํ๋ค.(๋น๋ฐ๋ฒํธ ํ๋ฆฌ๋๊ฑฐ 3๋ฒ๊น์ง ํ์ฉ)
2. sudo ์ด์ฉ์ ๋น๋ฐ๋ฒํธ ์๋ชป ์๋ ฅ์, custom message(๋ด๋ง๋๋ก) ๊ฐ ๋ณด์ฌ์ผ ํ๋ค.
3. sudo๋ฅผ ์ด์ฉํ action๋ค์ input ๊ณผ output์ด  archived(๋ชจ์ฌ์์ด์ผํจ). ๋ก๊ทธ ํ์ผ์ /var/log/sudo/ ํด๋์ ์ ์ฅ
4. ๋ณด์์ ์ธ ์ด์ ๋ก tty๋ชจ๋๋ ๊ฐ๋ฅํด์ผ ํ๋ค.
5. ๋ณด์์ ์ธ ์ด์ ๋ก the paths that can be used by sudo must be restricted.

    e.g. /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin


 ๊ฒฐ๊ตญ monitoring.sh๋ผ๋ ๊ฐ๋จํ ์คํฌ๋ฆฝํธ๋ฅผ ๋ง๋ค์์๊ฑด๋ฐ, bash๋ก ์คํ ๊ฐ๋ฅํด์ผํจ
์๋ฒ๊ฐ ์คํ๋๊ณ , ์ด ์คํฌ๋ฆฝํธ๋ ๋ชจ๋  ํฐ๋ฏธ๋์ ๋งค 10๋ถ๋ง๋ค ๋ช ๊ฐ์ง ์ ๋ณด๋ฅผ ํ์ํด์ผ ํฉ๋๋ค. (wall์ ์ฐธ๊ณ ํ์ธ์.)


OS ์ํคํ์ฒ์ ์ปค๋ ๋ฒ์ 

๋ฌผ๋ฆฌ์  ํ๋ก์ธ์์ ์

๊ฐ์ ํ๋ก์ธ์์ ์

์๋ฒ์์ ์ฌ์ฉ๊ฐ๋ฅํ RAM๊ณผ ์ฌ์ฉ๋ฅ (%๋ก ํ์)

์๋ฒ์์ ์ฌ์ฉ๊ฐ๋ฅํ ๋ฉ๋ชจ๋ฆฌ์ ์ฌ์ฉ๋ฅ (%๋ก ํ์)

ํ๋ก์ธ์์ ์ฌ์ฉ๋ฅ (%)

๋ง์ง๋ง์ผ๋ก ์ฌ๋ถํ๋ ๋ ์ง์ ์๊ฐ

LVM์ ํ์ฑ ์ฌ๋ถ

ํ์ฑํ ๋ ์ฐ๊ฒฐ์ ์

์๋ฒ๋ฅผ ์ฌ์ฉํ๋ ์ ์ ์ ์

์๋ฒ์ IPv4 ์ฃผ์์ MAC ์ฃผ์

`sudo`ย ํ๋ก๊ทธ๋จ์ผ๋ก ์คํ๋ ์ปค๋งจ๋์ ์
```

- ํ๊ฐ ์ค์, ์คํฌ๋ฆฝํธ๊ฐ ์ด๋ป๊ฒ ์คํ๋๋์ง ์ค๋ชํด์ผํฉ๋๋ค. ๊ทธ๋ฆฌ๊ณ  ์์ ํ์ง ์๊ณ  ์ค๋จํด์ผํฉ๋๋ค. cron์ ์ฐธ๊ณ ํ์ธ์.

---

# ํ๊ฐํ

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

Preliminaries ์ฌ์ ์ค๋น

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

  - ๋ณต์ ๋ ๋ฆฌํฌ์งํ ๋ฆฌ์ ๋ฃจํธ์ "signature.txt" ํ์ผ์ด ์๋์ง ํ์ธํฉ๋๋ค.

- Check that the signature contained in "signature.txt" is identical
  to that of the ".vdi" file of the virtual machine to be evaluated. A simple
  "diff" should allow you to compare the two signatures. If necessary, ask the
  student being evaluated where their ".vdi" file is located.
  - "signature.txt"์ ํฌํจ๋ ์๋ช์ด ํ๊ฐํ  ๊ฐ์ ์์คํ์ ".vdi" ํ์ผ์ ์๋ช๊ณผ ๋์ผํ์ง ํ์ธํฉ๋๋ค. ๋จ์ํ ใdiffใ๋ฅผ ์ฌ์ฉํ๋ฉด, 2๊ฐ์ ์๊ทธ๋์ฒ๋ฅผ ๋น๊ตํ  ์ ์์ต๋๋ค. ํ์์ ๋ฐ๋ผ์, ํ๊ฐ ๋์์ ํ์์๊ฒ ใ.vdiใํ์ผ์ ์์น๋ฅผ ๋ฌป์ต๋๋ค.
- As a precaution, you can duplicate the initial virtual machine in order
  to keep a copy.
- Start the virtual machine to be evaluated.
- If something doesn't work as expected or the two signatures differ,
  the evaluation stops here.

Mandatory part
The project consists of creating and configuring a virtual machine following strict rules. The student being evaluated will have to help you during the defense. Make sure that all of the following points are observed.

signature.txt์ ํฌํจ๋ ์๋ช์ด ํ๊ฐํ  ๊ฐ์ ์์คํ์ ".vdi" ํ์ผ์ ์๋ช๊ณผ ๋์ผํ์ง ํ์ธํฉ๋๋ค.
๊ฐ๋จํ "diff"๋ก ๋ ์๋ช์ ๋น๊ตํ  ์ ์์ต๋๋ค. ํ์ํ ๊ฒฝ์ฐ ํ๊ฐ ์ค์ธ ํ์์๊ฒ
".vdi" ํ์ผ์ด ์ด๋์ ์๋์ง ๋ฌป์ต๋๋ค.

Project overview

- The student being evaluated should explain to you simply:
- ๊ฐ๋จํ ์ค๋ชํ ์์์ด์ผํ๋ค.
- How a virtual machine works.
- ์ด๋ป๊ฒ ๊ฐ์๋จธ์ ์ด ์๋ํ๋์ง ?
- Their choice of operating system.
- ์ ํํ ์ด์ ์ฒด์ .
- The basic differences between CentOS and Debian.
- CentOS์ ๋ฐ๋น์์ ๊ธฐ๋ณธ์ ์ธ ์ฐจ์ด์ .
- The purpose of virtual machines.
- ๊ฐ์ ์์คํ์ ์ฉ๋
- If the evaluated student chose CentOS: what SELinux and DNF are.
- If the evaluated student chose Debian: the difference between
  aptitude and apt, and what APPArmor is.
  - ๋ง์ฝ ํ๊ฐ๋ ํ์์ด ๋ฐ๋น์: Apparmor๊ณผ apt์ ์ฐจ์ด, ๊ทธ๋ฆฌ๊ณ  APPArmor๊ฐ ๋ฌด์์ธ์ง ?
- During the defense, a script must display information all
  every 10 minutes. Its operation will be checked in detail later.
  If the explanations are not clear, the evaluation stops here.
- ์คํฌ๋ฆฝํธ์ ์ ๋ณด๊ฐ ๋ชจ๋ ํ์๋์ด์ผ ํฉ๋๋ค. 10๋ถ๋ง๋ค

---

Simple setup

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Ensure that the machine does not have a graphical environment at launch.
- gui๊ฐ ์ค์น์๋์ด์๋์ง ํ์ธ
- A password will be requested before attempting to connect to this machine.

  - ์ด ์ปดํจํฐ์ ์ฐ๊ฒฐ์ ์๋ํ๊ธฐ ์ ์ ์ํธ๊ฐ ํ์ํฉ๋๋ค.

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

- user jham์ด ์๋์ง ํ์ธํ๊ณ  ๊ทธ๊ฒ๋ค์ด sudo์ user42์ ์ํด์๋์ง ํ์ธ

Make sure the rules imposed in the subject concerning the password policy have been put in place by
following the following steps.

- ์ํธ๊ท์น์ด ์ ๋๋ก ๋์ด์๋์ง ํ์ธ

First, create a new user. Assign it a password of your choice, respecting the subject rules. The
student being evaluated must now explain to you how they were able to set up the rules requested
in the subject on their virtual machine.
Normally there should be one or two modified files. If there is any problem, the evaluation stops here.

- Now that you have a new user, ask the student being evaluated to create a group named "evaluating" in
  front of you and assign it to this user. Finally, check that this user belongs to the "evaluating" group.
- ์ด์  ์ ์ฌ์ฉ์๊ฐ ์๊ฒผ์ผ๋ ํ๊ฐ ๋์ ํ์์๊ฒ ์์ "evaluating"์ด๋ผ๋ ๊ทธ๋ฃน์ ๋ง๋ค์ด
  ์ด ์ฌ์ฉ์์๊ฒ ํ ๋นํ๋๋ก ์์ฒญํฉ๋๋ค. ๋ง์ง๋ง์ผ๋ก ์ด ์ฌ์ฉ์๊ฐ "evaluating" ๊ทธ๋ฃน์ ์ํ๋์ง ํ์ธํฉ๋๋ค.

- Finally, ask the student being evaluated to explain the advantages of this password policy, as well as the
  advantages and disadvantages of its implementation. Of course, answering that it is because the subject asks
  for it does not count.
- ๋ง์ง๋ง์ผ๋ก, ํ๊ฐ ๋์ ํ์์๊ฒ ๋น๋ฐ๋ฒํธ ์ ์ฑ์ ์ฅ์ ๊ณผ ๊ตฌํ์ ์ฅ์ ์ ์ค๋ชํ๋๋ก ์์ฒญํฉ๋๋ค.
  ๋ฌผ๋ก  ์ฃผ์ฒด๊ฐ ์๊ตฌํ๊ธฐ ๋๋ฌธ์ด๋ผ๊ณ  ๋๋ตํ๋ ๊ฒ์ ์ค์ํ์ง ์๋ค.
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

Hostname and partitions

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Check that the hostname of the machine is correctly formatted as follows: login42 (login of the student being evaluated).
- host์ด๋ฆ์ด 42์ธ์ง
- Modify this hostname by replacing the login with yours, then restart the machine. If on restart, the hostname has not been updated, the evaluation stops here.
- ํธ์คํธ์ด๋ฆ์ ๋ฐ๊พธ๊ณ  (์๋ฌด๊ฑฐ๋ ๋ฐ๊พธ๋ผ๋๊ฑด์ง ?) ๋ค์ ์์ํ์๋ ํธ์คํธ์ด๋ฆ์ด ๋ฐ๋์ด์ผํ๋ค.

- You can now restore the machine to the original hostname.
- ์ด์  ์์คํ์ ์๋ ํธ์คํธ ์ด๋ฆ์ผ๋ก ๋ณต์ํ ์์๋ค
- Ask the student being evaluated how to view the partitions for this virtual machine.
- Compare the output with the example given in the subject. Please note: if the
  student evaluated makes the bonuses, it will be necessary to refer to the bonus example.
- ํํฐ์ ๋ณด์ฌ์ฃผ๊ณ  ์๋ธ์ ํธ์ ๋น๊ต

- This part is an opportunity to discuss the scores! The student being evaluated should
  give you a brief explanation of how LVM works and what it is all about.
- Lvm์ ๋ํ ์ค๋ช, ๋์์๋ฆฌ
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

SUDO

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Check that the "sudo" program is properly installed on the virtual machine.
- sudo ์ค์น๋์ด์๋์ง ํ์ธ
- The student being evaluated should now show assigning your new user to the "sudo" group.
- ์์ฌ์ฉ์๋ฅผ sudo๊ทธ๋ฃน์ ํ ๋น ์ํค๋๊ฒ์ ๋ณด์ฌ์ค๋ผ
- The subject imposes strict rules for sudo. The student being evaluated must first explain the value and operation of sudo using examples of their choice.
  In a second step, it must show you the implementation of the rules imposed by the subject.
- sudo ๊ท์น์ ๋ํด์ ์ค๋ช
- Verify that the "/var/log/sudo/" folder exists and has at least one file. Check the contents of the files in this folder, You should see a history of the commands used with sudo.
- "/var/log/sudo/" ํด๋๊ฐ ์๊ณ  ํ์ผ์ด ํ๋ ์ด์ ์๋์ง ํ์ธํฉ๋๋ค. ์ด ํด๋์ ํ์ผ ๋ด์ฉ์ ํ์ธํ์ญ์์ค. sudo์ ์ฌ์ฉ๋ ๋ช๋ น์ด์ ๊ธฐ๋ก์ด ํ์๋ฉ๋๋ค.
- Finally, try to run a command via sudo. See if the file (s) in the "/var/log/sudo/" folder have been updated.
- sudo ๋ช๋ น์ ์คํํด์ ํ์ผ์ด ์๋ฐ์ดํธ๊ฐ ๋๋์ง ํ์ธ ์์ผ์ค๋ผ
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

UFW

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Check that the "UFW" program is properly installed on the virtual machine.
- UFW๊ฐ ์ค์น๋์ด ์๋์ง ํ์ธ
- Check that it is working properly.
- ์ ์์ ์ผ๋ก ์๋ ๋๋์ง ํ์ธ
- The student being evaluated should explain to you basically what UFW is and the value of using it.
- ํ๊ฐ ๋์ ํ์์ ๊ธฐ๋ณธ์ ์ผ๋ก UFW๊ฐ ๋ฌด์์ธ์ง, ๊ทธ๋ฆฌ๊ณ  UFW๋ฅผ ์ฌ์ฉํ๋ ๊ฐ์น์ ๋ํด ์ค๋ชํด์ผ ํฉ๋๋ค.
- List the active rules in UFW. A rule must exist for port 4242.
- UFW ํ์ฑ๊ท์น์ ๋์ด ?, ํฌํธ 4242๊ฐ ์์ด์ผํ๋ค. ๋ผ๋๊ฑฐ์ง ?
- Add a new rule to open port 8080. Check that this one has been added by listing the active rules.
- 8080ํฌํธ๋ฅผ ์ถ๊ฐํด์ ํ์ธ ์์ผ๋ผ
- Finally, delete this new rule with the help of the student being evaluated.
- ํ๊ฐ์ค์ธ ํ์์ ๋์์ ๋ฐ์์ ์ด ๊ท์น์ ์ญ์ ํด๋ผ ?
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

SSH

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

- Check that the SSH service is properly installed on the virtual machine.
- ssh๊ฐ ์ ๋๋ก ์ค์น๋์ด์๋์ง ํ์ธ
- Check that it is working properly.
- ์ ์์ ์ผ๋ก ์๋ํ๋์ง ํ์ธ
- The student being evaluated must be able to explain to you basically what SSH is and the value of using it.
- SSH๊ฐ ๋ฌด์์ด๊ณ  SSH๋ฅผ ์ฌ์ฉํ๋ ๊ฐ์น๋ฅผ ๊ธฐ๋ณธ์ ์ผ๋ก ์ค๋ชํ  ์ ์์ด์ผ ํฉ๋๋ค.
- Verify that the SSH service only uses port 4242.
- SSH ์๋น์ค๊ฐ ํฌํธ 4242๋ง ์ฌ์ฉํ๋์ง ํ์ธํฉ๋๋ค.
- The student being evaluated should help you use SSH in order to log in with the newly created user.
- ํ๊ฐ ์ค์ธ ํ์์ SSH๋ฅผ ์ฌ์ฉํ์ฌ ์๋ก ๋ง๋  ์ฌ์ฉ์๋ก ๋ก๊ทธ์ธํ๋ ๋ฐ ๋์์ด ๋ฉ๋๋ค.
- To do this, you can use a key or a simple password. It will depend on the student being evaluated.
- ์ด๋ ๊ฒ ํ๋ ค๋ฉด ํค๋ ๊ฐ๋จํ ์ํธ๋ฅผ ์ฌ์ฉํ๋ฉด ๋ฉ๋๋ค. ๊ทธ๊ฒ์ ํ๊ฐ๋ฐ๋ ํ์์ ๋ฐ๋ผ ๋ฌ๋ผ์ง ๊ฒ์๋๋ค.
- Of course, you have to make sure that you cannot use SSH with the "root" user as stated in the subject.
- ๋ฌผ๋ก  ์ ๋ชฉ์ ๋ช์๋ "๋ฃจํธ" ์ฌ์ฉ์์ SSH๋ฅผ ํจ๊ป ์ฌ์ฉํ  ์ ์๋๋ก ํด์ผ ํฉ๋๋ค.
- If something does not work as expected or is not clearly explained, the evaluation stops here.

---

Script monitoring

- Remember: Whenever you need help checking something, the student being evaluated should be able to help you.

The student being evaluated should explain to you simply:

- ๊ฐ๋จํ๊ฒ ์ค๋ชํด์ผํ๋ค.
- How their script works by showing you the code.
- ์ฝ๋๋ฅผ ๋ณด์ฌ์ค์ผ๋ก์จ ๊ทธ๋ค์ ์คํฌ๋ฆฝํธ๊ฐ ์๋ํ๋ ๋ฐฉ์.
- What "cron" is.
- cron์ด ์ด๋ค๊ฒ์ธ์ง ?
- How the student being evaluated set up their script so that it runs every 10 minutes from when the server starts.
- ํ๊ฐ ์ค์ธ ํ์์ด ์๋ฒ๊ฐ ์์๋  ๋๋ถํฐ 10๋ถ๋ง๋ค ์คํ๋๋๋ก ์คํฌ๋ฆฝํธ๋ฅผ ์ค์ ํ๋ ๋ฐฉ๋ฒ์๋๋ค.
- Once the correct functioning of the script has been verified, the student being evaluated should ensure that this script runs every minute.
- ๋งค๋ถ ๋ง๋ค ์คํ์ด ์๋๋์ง ํ์ธํด ๋ณผ๊ฒ
- You can run whatever you want to make sure the script runs with dynamic values correctly.
- Finally, the student being evaluated should make the script stop running when the server has started up, but without modifying the script itself.
- ๋ง์ง๋ง์ผ๋ก ํ๊ฐ ์ค์ธ ํ์์ ์๋ฒ๊ฐ ์์๋  ๋ ์คํฌ๋ฆฝํธ ์์ฒด๋ฅผ ์์ ํ์ง ์๊ณ  ์คํฌ๋ฆฝํธ ์คํ์ ์ค์งํด์ผ ํฉ๋๋ค.
- To check this point, you will have to restart the server one last time. At startup, it will be necessary to check that the script still exists in the same place, that its rights have remained unchanged, and that it has not been modified.
- ์ด ์ ์ ํ์ธํ๋ ค๋ฉด ์๋ฒ๋ฅผ ๋ง์ง๋ง์ผ๋ก ์ฌ์์ํด์ผ ํฉ๋๋ค. ์์ํ  ๋ ์คํฌ๋ฆฝํธ๊ฐ ์ฌ์ ํ ๊ฐ์ ์ฅ์์ ์กด์ฌํ๋์ง, ์คํฌ๋ฆฝํธ์ ๊ถํ์ด ๋ณ๊ฒฝ๋์ง ์์๋์ง, ์์ ๋์ง ์์๋์ง ํ์ธํด์ผ ํฉ๋๋ค.
- If something does not work as expected or is not clearly explained, the evaluation stops here.

๋ณธํฌ๋น ํ๊ฐ ๋
