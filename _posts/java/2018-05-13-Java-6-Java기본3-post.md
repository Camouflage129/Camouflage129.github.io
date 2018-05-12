---
layout: post
title: Java 기본 3
categories: [java]
---

**== Java 기본 정리 3==**<br>

10. Static, Final

∘Static : 클래스가 로딩될 때, 메모리 공간을 할당하는데 처음 설정된 메모리 공간이 변하지 않는다는 것을 말한다. 객체를 아무리 많이 만들어도 해당 변수는 하나만 존재한다.

⦁static 멤버 변수

클래스 변수라고도 부릅니다.

모든 해당 클래스는 같은 메모리를 공유합니다.

특정한 인스턴스에 종속되지 않습니다.

인스턴스를 만들지 않고 사용 가능합니다.

⦁static 메소드

클래스 메소드라고도 부릅니다.

오버라이드 불가합니다.

상속 클래스에서 보이지 않습니다.

⦁static 블록

클래스 내부에 만들 수 있는 초기화 블록입니다.

클래스가 초기화될 때 실행되고, main() 보다 먼저 수행됩니다.

⦁static import

다른 클래스에 존재하는 static 멤버들을 불러올 때 사용합니다.

멤버 메소드를 곧바로 사용할 수 있습니다.

 ∘Final : 해당 entity가 오로지 한 번 할당될 수 있음을 의미합니다.

⦁final 변수

해당 변수가 생성자나 대입연산자를 통해 한 번만 초기화 가능함을 의미합니다. 상수를 만들 때 응용합니다.

⦁final 메소드

해당 메소드를 오버라이드하거나 숨길 수 없음을 의미합니다.

⦁final 클래스

해당 클래스는 상속할 수 없음을 의미합니다. 문자 그대로 상속 계층 구조에서 ‘마지막’ 클래스입니다.

보안과 효율성을 얻기 위해 자바 표준 라이브러리 클래스에서 사용할 수 있는데, 대표적으로 java.lang.System, java.lang.String 등이 있습니다.

​     

11. 접근제한자 (pulbic＞protected > default > private)

⦁public – 접근 제한이 없다. (같은 프로젝트 내에 어디서든 사용가능하다.)

⦁protected – 같은 패키지 내, 다른 패키지에서 상속받아 자식클래스에서 접근 가능하다.

⦁default – 같은 패키지 내에서만 접근 가능하다.

⦁private – 같은 클래스 내에서만 접근 가능하다.

​     

12. Primitive type과 Reference type

⦁Primitive Type – 변수에 값 자체를 저장하는 타입을 말한다. 

​      Wrapepr Class를 통해 객체로 변형이 가능하다.

ex) int -> Integer, char -> Character

​     

⦁Reference Type – 메모리상에 객체가 있는 위치를 저장하는 타입을 말한다.

ex) Class, Interface, Array

​     

13. Wrapper Class

Primitive type으로 표현할 수 있는 데이터를 객체로 만들어주는 클래스를 말한다.

​     

14. Instanceof 연산자

A instanceof B의 결과값은 A->B 형변환이 가능할 시 True 그렇지 않으면 False가 return된다.

따라서 캐스팅이 가능한지 여부를 확인할 때 사용한다.

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}