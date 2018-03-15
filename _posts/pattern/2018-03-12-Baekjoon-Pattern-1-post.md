---

layout: post

title: 6064. 카잉 달력

categories: [pattern]

---

[백준 6064번 문제보러가기](https://www.acmicpc.net/problem/6064)

==**문제풀이 힌트**==<br>
M > N인 경우와 M < N인 경우를 나눠서 쭉 나열해보고 규칙을 찾자.<br>

```cpp
#include<iostream>
#include<algorithm>
#include<cmath>
using namespace std;

long long cal(int m, int n, int x, int y) {
	int temp = m - n;
	int cal = x % n;
	if (cal == 0)
		cal = n;
	if (temp == 0) {
		if (x != y)
			return -1;
	}
	else if (temp < 0) {
		for (int i = 1; i <= max(m, n); i++) {
			if (cal == y)
				return x + m * (i - 1);
			else {
				cal += temp;
				if (cal <= 0)
					cal += n;
			}
		}
		return -1;
	}
	else {
		for (int i = 1; i <= max(m, n); i++) {
			if (cal == y)
				return x + m * (i - 1);
			else {
				cal += temp;
				if (cal > n) {
					cal %= n;
					if (cal == 0)
						cal = n;
				}
			}
		}
		return -1;
	}
}

int main() {
	int m, n, x, y;
	int t;
	cin >> t;

	for (int i = 0; i < t; i++) {
		cin >> m;
		cin >> n;
		cin >> x;
		cin >> y;

		printf("%d\n", cal(m, n, x, y));
	}
}
```

**==풀이==**<br>
먼저 M < N인 경우,<br>
6 8 4 1 을 예를 들고 쭉 나열했을 경우 x,y는 다음과 같다.<br>
4 4 - 4 2 - 4 8 - 4 6 의 순서로 반복됨을 알 수 있다.<br>
이는 M과 N의 차이 만큼 떨어지면서 그 값이 음수인 경우<br>
다시 나머지 연산을 통해 시작하여 똑같은 방식으로 수행된다.<br>
이 때, 초기값이 그냥 X로 한다면, x와 y의 차이가 아주 큰 경우<br>
해당되지 않으므로 y의 초기값 또한 x를 N으로 나머지 연산한 값으로 한다.<br>
M > N인 경우는 이와 아주 유사하나 조금 반대의 성향을 가지므로<br>
위의 경우를 해결 한 다음 조금만 고치면 된다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}