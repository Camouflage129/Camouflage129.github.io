---
layout: post
title: JDBCUtil을 만들어 사용해보자.
categories: [java]
---

**== JDBCUtil 예제 ==**<br>

매번 Java에서 DB를 사용할 때 마다 Connection과 그 환경설정을 일일이 만들어야 한다면,<br>

그 불편함은 말로 할 수 없을것이다. JDBCUtil이라는 Class를 만들어 그 설정을 해주는 함수를 구축하고<br>

다른 클래스에서 편하게 써보도록 하겠다.<br>

먼저 C드라이브에 file이라는 폴더를 만들고 그 안에 dbinfo.txt파일을 만들자.<br>

이는 JDBC url, id, pw, driver등의 정보를 넣어 놓은 후 편하게 읽어와 수행하게 하기 위함이다.<br>

![1]({{ BASE_PATH }}images\java\JDBCUtil2.png)<br>

dbinfo는 다음과 같이 작성되야하며 뒤에 띄어쓰기가 하나만 있어도 바로 오류가 발생한다.<br>

![2]({{ BASE_PATH }}images\java\JDBCUtil3.png)<br>

이제 JDBCUtil 클래스를 만들어 보자.<br>

getConnection이라는 함수를 만들어 보도록 하자.<br>

먼저 Properties라는 클래스를 만들어 앞서 만들어 놓은 "c:/file:dbinfo.txt"를 load해 오자.<br>

이 후 Class.forName을 통해 DriverManager에 Properties에서 읽어온 드라이버를 등록하고,<br>

Connection에 DriverManager에서 Connection을 얻어오도록 한다.<br>

이 때, 아까 읽어온 Properties에서 해당되는 url, user, pw의 값을 읽어오도록 한다.<br>

마지막으로 Connection을 리턴해주면 getConnection 함수가 완성된다.<br>

<br>

이제 자원반납을 하는 close함수를 만들어 보자<br>

ResultSet, Statement, Connection이 null인 경우 할당이 안된 경우이므로<br>

null이 아닌경우에 자원반납을 하도록 한다.<br>

![3]({{ BASE_PATH }}images\java\JDBCUtil1.png)<br>

자 이제 다른 클래스에서 JDBCUtil을 이용하여 쿼리문을 수행해보도록 하자.<br>

엄청나게 길었던 코드를 단지, con = JDBCUtil.getConnection(); 을 통해 Connection을 할당받고<br>

이제 원하는 sql문을 수행하고 그 결과값을 받아보는 작업을 해보면 된다.<br>

예제 코드는 다음과 같다.<br>

![4]({{ BASE_PATH }}images\java\JDBCUtil4.png)<br>

-JDBCUtil를 활용해 Query수행해보기 끝-<br>



{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}