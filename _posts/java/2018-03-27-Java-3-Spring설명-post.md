---
layout: post
title: Spring이란?
categories: [java]
---

**== Spring이 무엇인지 알아보도록 하자. ==**<br>

먼저 스프링이란 무엇일까?<br>

스프링 프레임워크의 정의는 다음과 같다.<br>

- 자바(JAVA) 플랫폼을 위한 오픈소스(Open Source) 어플리케이션 프레임워크<br>
- 자바 엔터프라이즈 개발을 편하게 해주는 오픈 소스 경량급 애플리케이션 프레임워크<br>
- 자바 개발을 위한 프레임워크로 종속 객체를 생성해주고, 조립해주는 도구<br>
- POJO(Plain Old Java Object) BEAN CONTAINNER<br>

결국 간단히 말해서, 객체할당을 굉장히 간편하게 해주며, 이로인해 코드 간결화를 시킬 수 있다.<br>

또한, 가장 중요한 관점으로 오랫동안 사용되어 상당히 안정화되어있다는 점이다.<br>

스프링을 쓰지 않을 때 코드를 보도록 하자<br>

![ex1]({{ BASE_PATH }}images\java\MVC\ex1.png)<br>

각 Controller, Servlet를 일일이 만들어 줘야 하며,<br>

DispatcherServlet, HandlerMapping등 모두 다 만들어주어야한다.<br>

![HandlerMapping]({{ BASE_PATH }}images\java\MVC\HandlerMapping.png)<br>

이 처럼 맵을 통해 각 서블릿으로 보내주어야 하므로 굉장히 어려워진다.<br>

하지만 스프링을 통했을 때의 환경을 보자.

![ex2]({{ BASE_PATH }}images\java\MVC\ex2.png)<br>

각 컨트롤러가 하나에 모두 들어가며, Servlet과 HandlerMapping은 설정파일로 바뀌기 때문에<br>

클래스 파일이 현저게하 줄고,  객체생성을 직접하지 않으므로 코드가 매우 깔끔해진다.<br>

이제 Spring App단의 환경설정 파일을 보며 설정파일에서 어떻게 객체가 할당되는지 알아보자.<br>

![pring_Ap](C:\gitBlog\Camouflage129.github.io\images\java\MVC\Spring_App.png)<br>

ApplicationContext.xml은 App단의 클래스와 파일에 대한 설정이다<br>

Web단을 가지 않는 한 service에서 바로 View로 데이터 가공한 후 전송하기 때문에<br>

DAO와 Service에 관련된 설정이 들어간다는 것을 알 수 있다.<br>

먼저, DB부분부터 보도록 하자, 만약 MyBatis를 사용하고자 한다면,<br>

MyBatis-Config.xml이 필요하다 여기에는 Mapper가 등록되야하고<br>

Mapper는 Interface나 xml형태로 만들어서 MyBatis-Config.xml에 등록해놔야 한다.<br>

이제 위에서 DAOImpl 들을 보도록 하자. 각 Impl들은 Bean에 클래스경로와 ID를 등록한다.<br>

Spring을 이용한 DAO는 JDBCTemplate이 있어야하고<br>

할당 받을때는 @Autowired나 @Resources 그리고 Context.getBean("id")로 받을 수 있다.<br>

JDBCTemplate은 DataSource를 생성자나 Set메소드로 받아야 하므로<br>

c태그나 p태그를 사용하여 받아준 다는 것을 등록해놓자.<br>

근데 이 때, C태그나 P태그와 맞게끔 클래스에서 생성자나 Set메소드를 설정해놓아야한다.<br>

나머지의 구동방식도 마찬가지이다. 각 DAO는 사용하기위한 설정 클래스가 필요하고<br>

이 설정 클래스들 또한 앞서 필요한 파일들이 있다.<br>

그렇게 모두 등록해 놓은 후 Service나 xml에 설정된 bean을 사용할 때에는 <br>

위에서 언급한대로 @Autowired, @Resources, Context.getBean("id")로 받아야 한다.<br>

<br>

AOP에 대하여 알아보도록 하자.<br>

먼저 AOP는 Service와 Controller 중간에서 데이터의 흐름을 가로챌 수 있다.<br>

AOP에 등록된 서비스가 만약에 수행된다면,  먼저 Proxy가 만들어져서 Service를 호출하기 전에<br>

AOP를 무조건 거치게 된다. AOP를 거친 후 AOP 수행에 따라 Service를 수행하기도 하고 돌아가기도 한다.<br>



![pring_We](C:\gitBlog\Camouflage129.github.io\images\java\MVC\Spring_Web.png)<br>

Web단의 설정을 보도록 하자.<br>

Web.xml에는 App단의 설정파일과 Servlet설정파일 그리고 User와 Dispatcher Servlet사이에서<br>

그 요청을 가로채서 데이터를 가공하거나 처리할 수 있다.<br>

보통 UTF-8같은 처리 or 유효성검증을 하기도 한다.<br>

Dispatcher Servlet은 먼저 Servlet.xml파일로 그 내용이 설정되고 이 파일이 Web.xml에서 호출된다.<br>

Servlet.xml에서 Context Component-Scan은 HandlerMapping이 내재되어있기 때문에<br>

알아서 알맞은 Controller에 할당을 해준다.<br>

또한, Controller와 Dispatcher Servlet의 흐름을 가로채는 Interceptor를 여기에 등록해놓는다.<br>

Interceptor에서는 login이 안되어있는데 페이지를 들어가려하거나 하는 경우에<br>

login 세션의 값이 null인지 체크를 하여 되돌려 보내거나 처리를 하는 등으로 쓸 수 있다.<br>

Controller는 String과 ModelAndView를 통해 Dispatcher와 데이터를 주고 받는다.<br>

말 그대로 함수의 데이터 형이 String이거나 ModelAndView라는 뜻이다.<br>

Controller는 Web.xml에서 불러진 Application Context.xml에서 Service를 할당받는다.<br>

그리고 요청받은것에 따라 각 함수가 수행된다.<br>

<br>

이제 한꺼번에 설명하자면, 유저가 Request를 보내면 Filter가 Dispatcher에 가는 그 흐름을 가로채<br>

UTF-8로 그 형태를 바꿔주거나 유효성검증등을 해준다.<br>

이제, Web.xml에 등록된 Action-Servlet.xml파일에서 Context Coponent-Scan을 통해<br>

알맞은 Controller로 Request를 String 또는 ModelAndView를 통해 주고 받는다.<br>

이 과정에서 Action-Servlet.xml에 등록된 Interceptor가 그 흐름을 가로채<br>

login 세션등을 체크하여 Service를 수행하거나 페이지를 되돌려 보낼 수 있다.<br>

Controller에서 Service를 수행할 때에는, Web.xml에 등록된 Application-Context.xml<br>

을 부르고 그 안에 등록된 Service Bean을 할당하여 수행한다.<br>

이 때, 만약 Service가 AOP에 등록되어있다면 Proxy가 만들어져 Service를 수행하기전<br>

Proxy를 거쳐 AOP함수를 수행하게 된다. 이제 Service는 DAOImpl을 호출한다.<br>

역시 Application-Context.xml에 등록된 bean을 호출하여  DAOImpl을 수행하고<br>

DAOImpl은 DB와 연동될 때, Application-Context.xml에 설정된 각 설정파일을 통해<br>

DB에 접근하며 이 흐름은 끝난다.<br>

Spring Framework의 환경설정파일을 통해 구체적인 그 흐름을 보았다.<br>

설명이 개떡같아서 이해하는데 어려울 수 있으나 저 그림은 완벽하니<br>

잘 보면서 흐름을 숙달해 보자.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}