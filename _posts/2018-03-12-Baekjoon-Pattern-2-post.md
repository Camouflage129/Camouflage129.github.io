---

layout: post

title: 2292. 벌집

categories: [pattern]

---

[백준 2292번 문제보러가기](https://www.acmicpc.net/problem/2292)

==**문제풀이 힌트**==<br>
.<br>


```cpp
#include<iostream>
using namespace std;

long long check(long long input) {
	if (input == 1)
		return 1;
	for (long long i = 1; i <= 166666667; i++) {
		if (2 + 3 * i * (i-1) <= input && input < 2 + 3 * i * (i + 1))
			return ++i;
	}
}

int main() {
	long long input;
	cin >> input;

	input = check(input);
	printf("%lld \n", input);
}
```

**==풀이==**<br>
.<br>
{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}