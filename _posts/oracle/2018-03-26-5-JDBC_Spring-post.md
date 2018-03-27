---
layout: post
title: JDBC Spring
categories: [oracle]
---

**== JDBCUtil을 Spring을 통해 사용해 보자. ==**<br>

이 게시글에서는 JDBC를 xml설정 파일을 통해 dao와 service를 수행하는 방법에 대해 알아 볼 것이다.<br>

이 글을 보기전에 Java메뉴에서 MVC, Spring에 대한 글을 읽고 수행흐름을 파악한 후<br>

이 게시글을 보아야 무슨 내용인지 이해할 수 있을 것이다.<br>

<br>

Maven MVC Project를 만들어보는 것은 Tomcat을 깔고 테스트 할 때, 해보았다.<br>

만약 방법을 모른다면 <a href="https://camouflage129.github.io/Tomcat-3-MVC-Test-post">Maven MVC Project 만들기</a>를 보고 만들어 보자.<br>

<br>

Spring단을 배우려 한다면 클래스, 패키지 만드는 것은 굳이 보여주지 않아도 다 할것이다.<br>

Maven Project는 모든 라이브러리를 pom.xml에서 dependecy에 그 값을 추가하여 관리한다.<br>

다음 그림과 같이 JDBC 라이브러리를 추가해 주자<br>

![0]({{ Base_PATH }}images\oracle\spring\jdbc\0.png)<br>

depedency 값을 어디서 가져오나 궁금할만 한데,<br>

구글에 maven jdbc를 치면 가장 맨위에 나오는 사이트에 들어가서 복붙하면 된다.<br>

다른 라이브러리도 마찬가지로 'maven 라이브러리' 이름 을 검색하면 된다.<br>

자 이제, 라이브러리 설정이 끝났으므로 resources에서 applicationContext.xml을 만들자<br>![1]({{ Base_PATH }}images\oracle\spring\jdbc\1.png)<br>

![2]({{ Base_PATH }}images\oracle\spring\jdbc\2.png)<br>

![3]({{ Base_PATH }}images\oracle\spring\jdbc\3.png)<br>

위와 같이 만든 후에는 밑에서 Namespace를 클릭해 C태그를 넣어주자<br>

![5]({{ Base_PATH }}images\oracle\spring\jdbc\5.png)<br>

태그에 대한 설명을 하자면, p는 Set/Get메소드와 매칭이되고, c는 생성자와 매칭이된다.<br>

자 이렇게 하면 xml설정은 끝난다.

![6]({{ Base_PATH }}images\oracle\spring\jdbc\6.png)<br>

따라서 위와 같이 c:dao-ref= 로 생성자로 dao를 받는다고 한다면,<br>

반드시 그 클래스 안에 DAO 생성자가 있어야 한다.<br>

만약 set/get 메소드를 만든 후 설정한다면, 클래스안에 set/get메소드가 반드시 있어햐 할 것이다.<br>

![7]({{ Base_PATH }}images\oracle\spring\jdbc\7.png)<br>

자 이제 위의 그림과 같이 Service와 DAO Interface를 만들어주자 패키지 명도 지켜서 해주자<br>

![8]({{ Base_PATH }}images\oracle\spring\jdbc\8.png)<br>

이제 Impl class 파일들을 만들어주자<br>

DAOImpl은 위와 같으며 JDBC연동 할 때와 형태가 같다.<br>

![9]({{ Base_PATH }}images\oracle\spring\jdbc\9.png)<br>

자 위에서 설정한대로, dao는 new를 할 필요가 없다.<br>

왜냐하면 설정파일에서 생성자를 찾아 알아서 설정해놓은 bean에 따라 생성해 줄 것이기 때문이다.<br>

나중에 Annotation할당을 하면 Annotation만 붙여주면 생성자 마저도 필요없게 된다.<br>

(단, Default 생성자는 필요한 경우가 있다.)<br>

자 이제 JUnit Test를 통해서 잘 실행되는지 확인해 보자<br>

실제 개발할때에도 이렇게 함수를 짜고 JUnit을 통해 테스트 한 후 해야 설정에는 오류가 없으므로<br>

오류를 잡기가 편해지고 개발속도가 빨라진다.<br>

![10]({{ Base_PATH }}images\oracle\spring\jdbc\10.png)<br>

Properties에서 JUnit4 라이브러리를 추가해주자.<br>

![11]({{ Base_PATH }}images\oracle\spring\jdbc\11.png)<br>

new -> other에서 위의 경로로 들어가 JUnit Test를 생성해주자.<br>

![12]({{ Base_PATH }}images\oracle\spring\jdbc\12.png)<br>

setUp()함수는 테스트를 하기전 초기화를 하는 함수이고<br>

tearDown()은 테스트가 끝난 후 자원반납을 하는 함수이다.<br>

![13]({{ BASE_PATH }}images\oracle\spring\jdbc\13.png)<br>

자 Service또한 역시 ApplicationContext.xml에 설정해 놓았으므로 new를 통해 할당하지 않는다.<br>

String에서 config 파일이름을 읽어오고 그 파일 이름을 통해 ClassPath를 생성한다.<br>

자 이제, 설정해놓은 Bean id를 통해서 service를 할당한다.<br>

테스트 결과 아주 잘 수행되는 것을 볼 수있다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}