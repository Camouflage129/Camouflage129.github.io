---
layout: post
title: DataSource Spring
categories: [oracle]
---

**== DataSource Spring을 통해 사용해 보자. ==**<br>

앞선 JDBCUtil Spring의 글을 읽어야 추가적인 흐름이나<br>

기존에 추가된 라이브러리 파일을 볼 수 있으므로, 앞선 글을 읽고 읽는것을 추천한다.<br>

<br>

Spring단을 배우려 한다면 클래스, 패키지 만드는 것은 굳이 보여주지 않아도 다 할것이다.<br>

Maven Project는 모든 라이브러리를 pom.xml에서 dependecy에 그 값을 추가하여 관리한다.<br>

다음 그림과 같이 DataSource 라이브러리와 JDBCTemplate을 추가해 주자<br>

![1]({{ Base_PATH }}images\oracle\spring\datasource\1.png)<br>

자 이제, 라이브러리 설정이 끝났으므로 resources에서 applicationContext.xml설정을 해주자.<br>![2]({{ Base_PATH }}images\oracle\spring\datasource\2.png)<br>

갑자기 왜 굳이 DataSource를 쓰는지 JDBCUtil과의 차이점을 궁금해 할 수 있는데<br>

jdbc를 사용하여 db에 접속하기 위해서는 드라이버를 로드하고 <br>

db에 접속하여 connection 객체를 받아와야 한다. <br>

이런식이면 db에 쿼리를 보낼때 마다 드라이버를 로드하고 <br>

커넥션을 생성하고 닫게되는데 커넥션을 생성하고 다는데 시간이 소모되기에<br>

동시접속자가 많은 사이트의 경우 전체의 성능을 낮추는 원인이 된다.<br>

(드라이버도 한번만 로드하면 되는데 불필요하게 여러번 로드하게 된다)<br>

더 자세히 알고 싶다면 <a href="https://coffee-mark.tumblr.com/post/61383766496/%ED%86%B0%EC%BC%93%EC%97%90%EC%84%9C-datasource%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-db%EC%A0%91%EC%86%8D%EC%BB%A4%EB%84%A5%EC%85%98-%ED%92%80"> 다른 블로그</a>를 참고하도록 하자.<br>

<br>

무튼 위의 설명과 같은 이유로 DataSource를 bean에 등록한 후<br>

JDBCTemplate이 DataSource를 통해서 DB에 접근할 수 있기 때문에 c태그로 그 값을 받도록 하자<br>

자 이제, DAOImpl은 이제 단순히 생성자로 JDBCTemplate만 받으면 되고,<br>

코드가 얼마나 간결해지는지는 다음 사진에서 볼 수 있다.

![3]({{ Base_PATH }}images\oracle\spring\datasource\3.png)<br>

너무나 깔끔해진 것을 볼 수 있다. 감격...<br>

![4]({{ Base_PATH }}images\oracle\spring\datasource\4.png)<br>

DAO와 Service를 위와같이 만들어주자 List로 하는 이유는<br>

값이 여러개가 나오지는 않지만 DataSource Spring을 사용해서 할 경우<br>

RowMapper를 반드시 사용해야 하기 때문에 그 예시를 보여주려 한다.<br>

![5]({{ Base_PATH }}images\oracle\spring\datasource\5.png)<br>

?의 값을 중간에 있는 new Object[] {요기 안에} 순서에 맞춰 넣어주어야한다.<br>

그리고 RowMapper라는 것을 상속받아 VO객체라면 RowMapper\<VO>이런 식으로 바꿔야한다.<br>

그리고 return값은 항상 rs.get~으로 vo객체일 경우라면 vo를 생성하여 return해주면 되겠다.<br>

![6]({{ Base_PATH }}images\oracle\spring\datasource\6.png)<br>

서비스의 경우도 뭐 볼게 없다. 설정파일에서 생성자로 dao를 만드니 그 형태를 맞춰주자<br>

![7]({{ Base_PATH }}images\oracle\spring\datasource\7.png)<br>

자 이제 JUnit Test를 통해서 잘 실행되는지 확인해 보자<br>

Service또한 역시 ApplicationContext.xml에 설정해 놓았으므로 new를 통해 할당하지 않는다.<br>

String에서 config 파일이름을 읽어오고 그 파일 이름을 통해 ClassPath를 생성한다.<br>

자 이제, 설정해놓은 Bean id를 통해서 service를 할당한다.<br>

테스트 결과 아주 잘 수행되는 것을 볼 수있다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}