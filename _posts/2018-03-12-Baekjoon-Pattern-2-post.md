---

layout: post

title: 1475. 방 번호

categories: [pattern]

---

[백준 1475번 문제보러가기](https://www.acmicpc.net/problem/1475)

==**문제풀이 힌트**==<br>
6과 9가 여러개 있을 경우에만 다르게 계산한다.<br>

```cpp
#include<iostream>
#include<algorithm>
#include<string>
#include<cmath>
using namespace std;

long long distribute(string input) {
	long long num[8] = { 0 };
	for (long long i = 0; i < input.length(); i++) {
		long long temp = (input.at(i) - '0');
		if (temp == 9)
			num[6] += 1;
		else
			num[temp] += 1;
	}
	num[6] = (long long)ceil((double)num[6] / 2.0);
	sort(num, num + 8);
	return num[7];
}

int main() {
	long long input;
	cin >> input;

	printf("%lld\n", distribute(to_string(input)));
}
```

**==풀이==**<br>
1~9까지 들어갈 수 있는 배열을 만든다.<br>
그 배열안에서 가장 큰값을 추려내면 필요한 세트의 개수가 된다.<br>
이 때, 6과 9는 한 세트 안에 두개가 간주되므로 2로 나눈 후 올림을 해준다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}