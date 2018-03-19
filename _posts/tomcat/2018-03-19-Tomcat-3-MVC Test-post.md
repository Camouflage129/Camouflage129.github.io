---
layout: post

title: MVC 프로젝트 생성 후 서버 테스트

categories: [tomcat]

---

**== Spring MVC 프로젝트를 생성 후 서버를 테스트 해보자 ==**<br>

이번 글에서는 Spring MVC프로젝트를 생성 후 환경변수 설정을 해보고 서버 테스트를 해보겠다.<br>

![9]({{ BASE_PATH }}images\tomcat\9.png)<br>

마우스 우클릭 -> 프로젝트 -> Other로 가도록 하자<br>

![10]({{ BASE_PATH }}images\tomcat\10.png)<br>

Spring폴더 안에 Spring Legacy Project를 누르자.<br>

![11]({{ BASE_PATH }}images\tomcat\11.png)<br>

project 이름을 입력하고 Spring MVC Project를 선택한 후 다음으로 넘어가자<br>

![12]({{ BASE_PATH }}images\tomcat\12.png)<br>

프로젝트의 이름을 만들어주는 부분으로 com.biz.OOO 기업명을 적기도 한다.<br>

![13]({{ BASE_PATH }}images\tomcat\13.png)<br>

이제 생성된 프로젝트를 우클릭하여 Properties에서 환경변수를 설정해 보자.<br>

![14]({{ BASE_PATH }}images\tomcat\14.png)<br>

먼저 Java Build Path에서 자신이 설치한 JDK와 맞는 자바버전으로 바꾸어주도록 한다.<br>

![15]({{ BASE_PATH }}images\tomcat\15.png)<br>

필자의 경우에는 1.9버전이므로 위의 사진과 같이 나타난다.<br>

![16]({{ BASE_PATH }}images\tomcat\16.png)<br>

다음은 Java Compiler에서 컴파일러 버전을 위의 선택한 JDK버전과 같게 맞춰주도록 한다.<br>

![17]({{ BASE_PATH }}images\tomcat\17.png)<br>

Project Facets에서 역시 JDK버전과 같게 맞추어 주도록 하자<br>

![18]({{ BASE_PATH }}images\tomcat\18.png)<br>

다음은 Server에서 Tomcat을 클릭후 Apply를 눌러 적용시켜주자.<br>

![19]({{ BASE_PATH }}images\tomcat\19.png)<br>

Targeted Runtimes에서 아까 설정해준 Server를 클릭한 후 Apply를 해주자.<br>

이제 환경변수 설정이 끝났으므로 모두 적용을 눌러주고 꺼준다.<br>

![20]({{ BASE_PATH }}images\tomcat\20.png)<br>

이제 프로젝트에서 우클릭한 후 Rus As -> Run on Server를 클릭하여 서버를 실행시켜주자.<br>

![21]({{ BASE_PATH }}images\tomcat\21.png)<br>

서버설정이 정상적으로 수행되었고, MVC도 정상적으로 환경변수 설정이 끝난 상태이다.<br>

먼저 설정해준 9000번 포트로 연결된 것을 볼 수 있다. - 아파치 설정 끝 -<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}