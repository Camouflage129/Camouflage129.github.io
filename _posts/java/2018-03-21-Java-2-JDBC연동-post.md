---
layout: post
title: JDBC연동
categories: [java]
---

**== Eclipse에서 JDBC연동 후 쿼리를 수행해보자. ==**<br>

먼저 자바 프로젝트를 만든 후 우클릭하여 Properties 환경설정을 해주자<br>

![1]({{ BASE_PATH }}images\java\JDBC1.png)<br>

Java Build Path에서 Libraries에서 Add External JARs를 누른 후<br>

Oracle DB연동시 사용했던 Ojdbc6.jar를 추가하자. 파일경로도 똑같다.<br>

![2]({{ BASE_PATH }}images\java\JDBC2.png)<br>

이제 클래스파일을 만들어 보고 수행할 텐데 먼저 설명을 하도록 하겠다.<br>

먼저, Class.forName("드라이버 명")을 통해 Oracle드라이버를 호출 한다.<br>

이 때, DriverManager에 해당 Driver가 자동등록되고 따라서 Connection을 얻어 쓸 수 있게 된다.<br>

(이 때, 만약 Driver 클래스가 없다면 ClassNotFoundException이 발생한다.)<br>

이제 Connection 을 DriverManager에서 getConncetion(url,user,pw)로 부터 받아 선언한다.<br>

이렇게 얻은 Connection으로부터 이제 Statement를 받아 Sql을 수행하고 결과를 받을 수 있다.<br>

하지만 보안상 Statement가 매우 취약하므로 PreStatement를 사용하도록 하자.<br>

PreStatement는 Connection을 통해 Sql문을 수행할 수 있고 이 때, 필요한 조건문에 들어갈 값은<br>

?로 표시한 후 PreStatement에서 설정하여 Sql문을 수행해주도록 한다.<br>

ResultSet은 PreStatement가 수행한 Sql문의 결과 값을 받아오며, <br>

next함수로 부터 getString / Date / int 등 구체적으로 해당 컬럼에 대해 값을 받아 올 수 있다.<br>

마지막으로 finally에서 반드시 자원을 반납해 주도록 한다.<br>

간단한 예제 코드는 다음과 같다.<br>

![3]({{ BASE_PATH }}images\java\JDBC3.png)<br>

-JDBC 연동하여 DB수행하기 끝-<br>



{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}