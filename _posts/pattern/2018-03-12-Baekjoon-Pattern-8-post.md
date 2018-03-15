---

layout: post

title: 2292. 벌집

categories: [pattern]

---

[백준 2292번 문제보러가기](https://www.acmicpc.net/problem/2292)

==**문제풀이 힌트**==<br>
1칸 이동하는 첫번째 수 - 2칸 이동하는 첫번째 수 이런식으로 수열을 만들어보자.<br>


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
힌트를 이용한다면 계차수열이 만들어진다.<br>
An : 2 - 8 - 20 - 38 - ...<br>
Bn : 6 - 12 - 18 - ...<br>
따라서 An = 2 + Sum(Bn) = 2 + Sum(6 + 6(k-1)) = 3n^2 - 3n이 된다.<br>
(위에서 Sum 은 시그마를 의미함)<br>
{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}