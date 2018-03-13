---

layout: post

title: 1924. 2007년

categories: [pattern]

---

[백준 1924번 문제보러가기](https://www.acmicpc.net/problem/1924)

==**문제풀이 힌트**==<br>
각 달이 몇일까지 있는지 파악하고<br>
그 달들의 요일 수와 요일에 대한 패턴을 알아낸다<br>
필자는 7로 나눈 나머지로 문제를 풀었다.<br>

```cpp
#include<iostream>
using namespace std;

int cal_day(int m, int d, int c_m, int c_d) {
	if (m == c_m && m != 1)
		return (c_d + d) % 7;
	else if (m == 1)
		return d % 7;
	else {
		if (c_m == 1 || c_m == 3 || c_m == 5 || c_m == 7 || c_m == 8 || c_m == 10 || c_m == 12)
			cal_day(m, d, ++c_m, c_d + 31);
		else if (c_m == 2)
			cal_day(m, d, ++c_m, c_d + 28);
		else if (c_m == 4 || c_m == 6 || c_m == 9 || c_m == 11)
			cal_day(m, d, ++c_m, c_d + 30);
	}
}

void result(int d) {
	if (d == 1)
		printf("MON\n");
	else if (d == 2)
		printf("TUE\n");
	else if (d == 3)
		printf("WED\n");
	else if (d == 4)
		printf("THR\n");
	else if (d == 5)
		printf("FRI\n");
	else if (d == 6)
		printf("SAT\n");
	else if (d == 0)
		printf("SUN\n");
	else
		printf("Error\n");
}


int main() {
	int m,d;
	cin >> m;
	cin >> d;

	result(cal_day(m, d, 1, 0));
}
```

**==풀이==**<br>
입력받은 월이 몇일까지 있는지 판단한다.<br>
그리고 각 일수를 각 월의 총 일수를 더해서<br>
7로 나눈 나머지를 구하면 0~7의 값을 얻을 수 있다.<br>
그리고 0~7까지 일요일 - 월요일 -... 순임도 알 수 있다.<br>
예를들어,<br>
31일까지 있는 월은 입력받은 일 수에 31일을 더하고<br>
7로 나눈 나머지를 구하면 그 값이 1일 때 월요일 임을 알 수 있다.<br>
{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}