---

layout: post

title: 1011. Fly me to the Alpha Centauri
categories: [pattern]

---

[백준 1011번 문제보러가기](https://www.acmicpc.net/problem/1011)

<문제풀이 힌트>
이 문제의 경우 규칙을 찾는 것이 가장 중요하다.
일자로 쭉 나열 해 보면,
n^2의 수열에서 최단거리 = 좌우대칭이 완벽한 구조임을 알 수 있다.
이제 n^2의 수열과 나머지 수의 규칙을 찾아서 문제를 풀면 된다.

- - -

```cpp
#include<iostream>
#include<math.h>
using namespace std;

long long getNum(long long num) {
	for (long long i = 1; i < num; i++) {
		long long an_1 = (long long)pow(i - 1, 2);
		long long an = (long long)pow(i, 2);
		long long length = an - an_1;
		if (an - i < num && num <= an)
			return length;
		else if (an < num && num <= an + i)
			return length + 1;
	}
}

int main() {
	long long x, y;
	int t;
	cin >> t;
	for (int i = 0; i < t; i++) {
		cin >> x;
		cin >> y;

		printf("%lld\n", getNum(y - x));
	}
}
```

- - -

<풀이>
An = n^2이라 하면, An의 최단거리는 An - An-1 임을 알 수 있다.
또한 An - (n-1) ~ An은 같은 거리를 갖고 
An ~ An + n 까지는 An의 최단거리 +1이 됨을 알 수 있다.
예를 들면,
n=3 일 때, 7~9 까지는 거리가 모두 5이나 10~12 까지는 거리가 6임을 볼 수 있다.
그리고 이 문제에서 가장 중요한 점은 어디까지 반복문을 수행하느냐 인데,
위 소스에서 i < num을 하지 않을 경우 저어엉말 끔찍한 틀렸습니다의 연속을 맛 볼 수있다.


{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}