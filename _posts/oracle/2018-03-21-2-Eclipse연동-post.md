---
layout: post
title: Eclipse와 Oracle DB를 연동해보자.
categories: [oracle]
---

**== Eclipse와 Oracle DB 연동 ==**<br>

이제 Scott계정을 설정해보자.<br>

sql문은 @C:\oraclexe\app\oracle\product\11.2.0\server\rdbms\admin\scott.sql 이다.<br>

이 후 비밀번호 변경 까지 해준 후 Scott 계정으로 들어간다.<br>

![9]({{ BASE_PATH }}images\oracle\설치\설치9.png)<br>

Scott계정이 정상적으로 설정되었는지 Table을 조회해보자.

![10]({{ BASE_PATH }}images\oracle\설치\설치10.png)<br>

정상적으로 DB가 설정이 끝났으므로  Eclipse와 연동을 해보자 <br>

![11]({{ BASE_PATH }}images\oracle\연동\연동1.png)<br>

우측 상단 모서리 JAVAEE를 누른 후 하단 Data Source Explorer에서 우클릭 new를 한 후<br>

Oracle Driver를 눌러주고 Name을 Scott으로 해준 후 넘어가자.<br>

![12]({{ BASE_PATH }}images\oracle\연동\연동2.png)<br>

Drivers옆에 설정 아이콘을 누르자.<br>

![13]({{ BASE_PATH }}images\oracle\연동\연동3.png)<br>

Oracle Thin Driver 11을 선택한 후 JAR List로 넘어가자.<br>

![14]({{ BASE_PATH }}images\oracle\연동\연동4.png)<br>

Add  JAR/Zip으로 들어가서  C:/oraclexe/app/oracle/product/11.2.0/server/jdbc/lib로 들어간 후<br>

ojdbc6.jar를 선택해 주자 참고로 이 jar파일은 나중에 또 사용될 것이므로 <br>

lib폴더를 따로 만들어 관리해주는 것도 나쁘지않다.<br>

이제 Properties탭으로 넘어가자.<br>

![15]({{ BASE_PATH }}images\oracle\연동\연동5.png)<br>

URL, Database Name, Pw, ID등을 다음과 같이 정확하게 입력해 준다.<br>

![16]({{ BASE_PATH }}images\oracle\연동\연동6.png)<br>

Test_Connetion을 눌러 다음과 같이 Ping이 성공적으로 수행된다면<br>

제대로 설정된 것이다. 이제 Next->Finish를 누르자<br>

![17]({{ BASE_PATH }}images\oracle\연동\연동7.png)<br>

이제 하단을 보면 Scott계정이 정상적으로 연동된 것을 볼 수있다.<br>

이제 Sql파일을 만들어 Java에서 수행하도록 해보자.<br>

![18]({{ BASE_PATH }}images\oracle\연동\연동8.png)<br>

Sql파일을 만들자.<br>

![19]({{ BASE_PATH }}images\oracle\연동\연동9.png)<br>

Sql파일을 만들 때, 우리가 설정 해놓은 DB와 완벽하게 맞춰서 셋팅해 준다.<br>

![20]({{ BASE_PATH }}images\oracle\연동\연동10.png)<br>

다음과 같이 설정이 잘 되었는지 상단에서 확인하고 단축키를 모를 경우<br>

쿼리문을 입력한 후 마우스 우클릭을 통해 다음과 같이 실행해보자.<br>

![21]({{ BASE_PATH }}images\oracle\연동\연동11.png)<br>

쿼리문이 정상적으로 수행된 것을 볼 수있다.<br>

참고로 Eclipse에서 실행하는 쿼리문은 모두 Auto Commit처리 되기 때문에 주의하도록 한다.<br>

![22]({{ BASE_PATH }}images\oracle\연동\연동12.png)<br>

-Oracle  Eclipse 연동 끝-<br>

JDBC연동과 이 후는 JAVA 메뉴에서 알아보도록 하자.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}

