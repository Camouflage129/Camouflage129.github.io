---

layout: post

title: 10250. ACM 호텔

categories: [pattern]

---

[백준 10250번 문제보러가기](https://www.acmicpc.net/problem/10250)

==**문제풀이 힌트**==<br>
몫과 나머지를 이용하여 푼다.<br>

```cpp
#include<iostream>
#include<cmath>
using namespace std;

int calculate(int h, int w, int n) {
	double num = (double)n / (double)h;
	num = ceil(num);
	int floor = n % h;
	if (floor == 0)
		floor = h;
	return (floor * 100) + num;
}

int main() {
	int h, w, n;
	int t;
	cin >> t;
	for (int i = 0; i < t; i++) {
		cin >> h;
		cin >> w;
		cin >> n;
		printf("%d\n", calculate(h, w, n));
	}
}
```

**==풀이==**<br>
층의 수는 높이에서 입력받은 n의 값을 나눴을 때 몫이다.<br>
단, 주의할 점은 높이와 n의 값이 딱 나누어 떨어질 때를 제외하고 숫자가 정수가 아니므로<br>
double로 계산을 수행하고, ceil로 무조건 올림을 수행하여 값을 제대로 만들어주어야한다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}