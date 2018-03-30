---
layout: post
title: Eclipse 설치 및 Java 환경변수 설정
categories: [java]
---

**== Eclipse설치와 Java 환경변수를 설정해보자. ==**<br>

먼저, <a href="https://eclipse.org/downloads">Eclipse 다운로드 페이지</a>로 가자.<br>

밑에 Download Packages를 선택해야 zip종류의 파일을 받을 수 있다.<br>

![1]({{ BASE_PATH }}images\java\설치\1.png)<br>

EE Developers를 윈도우 버전에 맞게 설치하자.<br>

![2]({{ BASE_PATH }}images\java\설치\2.png)<br>

![3]({{ BASE_PATH }}images\java\설치\3.png)<br>

이클립스를 다운 후 압축을 풀어주고, 이제 Java JDK를 설치하자<br>

<a href="https://www.oracle.com">Oracle홈페이지</a>로 이동하자.

![4]({{ BASE_PATH }}images\java\설치\4.png)<br>

Java for Developers로 들어가자.<br>

![5]({{ BASE_PATH }}images\java\설치\5.png)<br>

자신에게 맞는 JDK버전을 다운로드 받아주자.<br>

![6]({{ BASE_PATH }}images\java\설치\6.png)<br>

동의하고 윈도우 버전에 맞게 다운로드 받아주자.<br>

![7]({{ BASE_PATH }}images\java\설치\7.png)<br>

JDK를 다운 받은 후 설치해주고 이제 환경변수를 설정해보자.<br>

고오급 시스템 설정에 들어간 후<br>

![9]({{ BASE_PATH }}images\java\설치\9.png)<br>

환경변수를 클릭<br>

![10]({{ BASE_PATH }}images\java\설치\10.png)<br>

JDK가 설치된 파일의 경로를 복사 한 후<br>

![11]({{ BASE_PATH }}images\java\설치\11.png)<br>

아까 열어놓은 환경변수에서 다음과 같이 추가해주자.<br>

Path는 맨 앞에 %JAVA_HOME%\bin;을 추가해주고,<br>

 JAVA_HOME은 새로만들어 아까 복사해놓은 경로를 입력해준다.<br>

![12]({{ BASE_PATH }}images\java\설치\12.png)<br>

잘 입력되었는지 확인하기 위해 콘솔창에서 다음과 같은 명령어를 실행해본다.<br>

하나도 빠짐없이 잘 실행된다면 환경변수 설정이 잘 된것이다.<br>

![13]({{ BASE_PATH }}images\java\설치\13.png)<br>

-Eclipse 설치 및 Java환경변수 설정 끝-<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}