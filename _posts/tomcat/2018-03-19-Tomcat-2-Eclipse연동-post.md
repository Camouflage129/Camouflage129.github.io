---
layout: post

title: Eclipse와 서버 연동하기

categories: [tomcat]

---

**== Eclipse와 연동해 보자. ==**<br>

이번 글에서는 이클립스에서 서버연동을 하는 과정을 담고 <br>

다음 글에서  MVC프로젝트를 생성한 후 서버연동이 잘 되었는지 테스트 해보도록 하겠다.<br>

Spring 설치 및 MVC프로젝트에 대해서는 Java 메뉴안에 상세히 올리도록 할 예정이다.<br>

![6]({{ BASE_PATH }}images\tomcat\6.png)<br>

먼저 이클립스를 키고 하단 메뉴에서 서버를 클릭후 우측마우스를 클릭하자.<br>

위의 그림과 같은 형태가 나올 것이고 new -> server를 눌러 서버를 만들자<br>

![7]({{ BASE_PATH }}images\tomcat\7.png)<br>

메뉴에서 위로올리다보면 Apache가 있을테고 아파치를 클릭하여 설치한 버전의 Tomcat을 고른다.<br>

![8]({{ BASE_PATH }}images\tomcat\8.png)<br>

Next로 넘기고 해당 화면에서 Browse를 하여 아까 C에서 압축풀었던 tomcat폴더를 누르자<br>

이 때, 반드시 bin 상위폴더를 선택하여야 한다.<br>

이렇게 까지가 Eclipse에서 서버를 연동한 부분이다.<br>

다음 글에서 Spring MVC프로젝트를 생성하고 환경변수 설정을 한 후 테스트 해보도록 하자.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}