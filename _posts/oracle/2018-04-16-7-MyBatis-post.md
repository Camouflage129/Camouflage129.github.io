---
layout: post
title: MyBatis
categories: [oracle]
---

**== MyBatis를 사용해 보자. ==**<br>

먼저 MyBatis는 무엇인가? <br>

MyBatis는 개발자가 지정한 SQL, 저장프로시저, 매핑을 지원하는 프레임워크이다.<br>

MyBatis는 JDBC로 처리하는 상당부분의 코드와 파라미터 설정 및 결과 매핑을 대신해준다.<br>

또한 DB 레코드 원시타입과 Map 인터페이서, 자바 POJO를 설정해 매핑하기 위해서<br>

XML과 Annotation을 사용할 수 있다.<br>

<br>

이제, MyBaits를 구현하기 위해 필요한 것을 알아보자<br>

1. XML 설정파일이 필요하다 위에서 언급했듯이,<br>

   MyBatis의 전반적인 정보가 담긴 설정파일이 필요하다.<br>

2. Mapper.xml 파일 작성하기<br>

   인자값 매핑과 결과값 매핑 정보를 포함한 Sql문을 작성하는 곳이다.<br>

3. SqlSessionFactory 빌드를 통해 DAO를 구현한다.<br>

여기서 보여지는 사진들은 대다수가 홍승길 강사님의 수업 스크린샷이다.<br>

감사합니다. -꾸벅-<br>

DB연결이 밑에서는 MySql을 사용하지만<br>

이것을 보고 Oracle과 다르다고 적용을 못한다면 컴퓨터를 하는것에 심히 고민을해보자<br>

먼저, MyBatis 라이브러리가 필요하므로 pom.xml에 등록해주자.<br>

![1]({{ Base_PATH }}images\oracle\mybatis\1.png)<br>

참고로 밑에 spring은 이 후 Annotation설정을 할 때 필요하고 지금은 당장 필요하지않다.<br>

자 이제 MyBaits-Config.xml 파일을 만들어주자.<br>

![2]({{ Base_PATH }}images\oracle\mybatis\2.png)<br>

설정파일의 최상의 태그는 configuration이다.<br>

여기서 DB연결정보, 매퍼파일의 위치, VO 클래스의 위치와 닉네임설정이 꼭 필요하다.<br>

![3]({{ Base_PATH }}images\oracle\mybatis\3.png)<br>

![4]({{ Base_PATH }}images\oracle\mybatis\4.png)<br>

여기서 이 후,  Annotation설정을 하게 되면, 우리가 미리 등록해놨던 DataSource를 통해서<br>

DB연결정보를 받아올 수 있다는 점을 기억하자. 나중에는 작성하지 않아도 되는 부분이다.<br>

![5]({{ Base_PATH }}images\oracle\mybatis\5.png)<br>

![6]({{ Base_PATH }}images\oracle\mybatis\6.png)<br>

![7]({{ Base_PATH }}images\oracle\mybatis\7.png)<br>

![8]({{ Base_PATH }}images\oracle\mybatis\8.png)<br>

![9]({{ Base_PATH }}images\oracle\mybatis\9.png)<br>

![10]({{ Base_PATH }}images\oracle\mybatis\10.png)<br>

![11]({{ Base_PATH }}images\oracle\mybatis\11.png)<br>

![12]({{ Base_PATH }}images\oracle\mybatis\12.png)<br>

자 이로써 config의 설정이 끝났다.<br>

Mapper 설정파일을 작성해보자.<br>![13]({{ Base_PATH }}images\oracle\mybatis\13.png)<br>

![14]({{ Base_PATH }}images\oracle\mybatis\14.png)<br>

![15]({{ Base_PATH }}images\oracle\mybatis\15.png)<br>

![16]({{ Base_PATH }}images\oracle\mybatis\16.png)<br>

![17]({{ Base_PATH }}images\oracle\mybatis\17.png)<br>

![18]({{ Base_PATH }}images\oracle\mybatis\18.png)<br>

![19]({{ Base_PATH }}images\oracle\mybatis\19.png)<br>

![20]({{ Base_PATH }}images\oracle\mybatis\20.png)<br>

![21]({{ Base_PATH }}images\oracle\mybatis\21.png)<br>

![22]({{ Base_PATH }}images\oracle\mybatis\22.png)<br>

여기서 $는 보안상 위험한 특성이있다. <br>

왜냐면 값을 그대로 가져오기 때문에, 누가 Injection을 한다면,<br>

쉽게말해 쿼리문을 적고 그 뒤에 부분을 주석처리문장으로 보내버리면<br>

내가 작성해 놓은 쿼리문이 아닌 해커가 얻고자 하는 정보를 추출해 내기 때문이다.<br>

이제 매퍼 설정이 끝났다.<br>

이제 MyBatis를 사용해 보도록 하자.<br>

맨 처음 말했던 3번째 단계이다<br>

![23]({{ Base_PATH }}images\oracle\mybatis\23.png)<br>

![24]({{ Base_PATH }}images\oracle\mybatis\24.png)<br>

![25]({{ Base_PATH }}images\oracle\mybatis\25.png)<br>

![26]({{ Base_PATH }}images\oracle\mybatis\26.png)<br>

![27]({{ Base_PATH }}images\oracle\mybatis\27.png)<br>

![28]({{ Base_PATH }}images\oracle\mybatis\28.png)<br>

![29]({{ Base_PATH }}images\oracle\mybatis\29.png)<br>

MyBatis 연동 끝<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}