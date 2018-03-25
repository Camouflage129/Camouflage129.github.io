---
layout: post
title: MVC란?
categories: [java]
---

**== MVC가 무엇인지 알아보도록 하자. ==**<br>

MVC는 기본적으로 Model View Controller의 약자로<br>

프로그램 개발 시 세가지 역할로 구분하여 개발하는 방법론이다. <br>

이렇게 하는 이유는 완벽한 분업화를 통해<br>

해당 역할 개발자가 자신의 역할에만 집중하여 개발 하기 위함이다.<br>

![MVC]({{ BASE_PATH }}images\java\MVC\mvc.png)<br>

위의 그림을 보고 MVC가 분업화를 어떻게 이루는지 설명해 보도록 하겠다.<br>

먼저, App개발시에는 Controller단은 Service까지가 개발의 끝이고, <br>

Web단으로 갔을 때, 위의 그림 처럼 각 기능을 수행할 Controller와 <br>

사용자의 요청에 따라 그것을 제어해 줄 Dispatcher Servlet 그리고<br>

다시 반환 할 때, 알맞은 JSP로 보내줄 Map Resovler가 존재한다. <br>

(Map Resolver는 위의 그림에 그리지 않았습니다.)<br>

<br>

먼저, DB개발자와 서버(Controller)개발자는 <br>

서로 필요한 데이터를 어떠한 함수에 적절한 인자를 넣어서 주고받을지 정한다.<br>

이러한 함수를 정의한 곳이 Interface로 이루어진 DAO와 Service이다.<br>

<br>

Interface 설계가 끝났다면, 각 개발자는 짜여진 Interface를 보고 그 기능을 구현한다.<br>

이렇게 그 기능이 구현 된 클래스가 Impl 클래스이다.<br>

이렇게 구현된 Impl 클래스를 통해서 Controller 개발자는 DB의 대한 코드를 하나도 보지않고<br>

그저 DAO.funcA();를 호출해 그 기능을 수행한다. 이 때, 만약 오류가 발생한다면<br>

오류 코드에는 DAO.funcA()에 대하여 오류가 나기 때문에<br>

Service개발자는 DB개발자에게 해당 함수에 대하여 오류를 해결해달라 하면 된다.<br>

이로써 자신들이 해야 할 업무에만 집중하여 개발할 수 있는 형태가 만들어진다.<br>

나머지 경우는 말하지 않아도 충분히 이해가 갔으리라 판단한다.<br>

다음 게시글에서는 MVC2구조, Spring / Framework에 대해 알아 보도록 하자.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}