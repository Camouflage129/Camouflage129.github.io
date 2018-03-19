---
layout: post

title: Tomcat 다운로드 및 설치

categories: [tomcat]

---

**== 톰켓을 설치해 보자==**<br>

<a href="http://tomcat.apache.org/">톰켓 홈페이지</a> 에 들어가면 다음과 같은 화면에서 좌측 메뉴를 보자.<br>

![1]({{ BASE_PATH }}images\tomcat\1.png)<br>

위에서 빨간 부분을 클릭하여 다운로드 페이지로 간 후 밑으로 드래그를 하면<br>![2]({{ BASE_PATH }}images\tomcat\2.png)<br>

8.0버전 자신에 맞는 윈도우zip파일을 다운로드 받자.<br>

![3]({{ BASE_PATH }}images\tomcat\3.png)<br>

C드라이버에 tomcat폴더를 만들어 준 후 그 안에 압축을 풀자.<br>

![4]({{ BASE_PATH }}images\tomcat\4.png)<br>

반드시 바꿔줘야 할 설정이 있는데, 후에 오라클DB를 설치하면 포트번호가 8080으로 겹쳐<br>

문제가 발생할 수 있으므로 9000번으로 바꿔주는 설정을 할 것이다.<br>

C:\tomcat\apache-tomcat-8.0.50\conf 로 들어간 후 server.xml파일을 열자<br>

![5]({{ BASE_PATH }}images\tomcat\5.png)<br>

원래 저 부분이 8080으로 되어있을 텐데 9000번으로 바꾸어 사용하자<br>

이클립스에서 바꿔도 되나 이클립스에서 수정시 매 프로젝트마다 수정해주어야 하므로<br>

직접 여기서 바꿔주는 것이 좋다.<br>

다음 글에서 이클립스에서 서버연동하는 과정을 보도록 하자.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}