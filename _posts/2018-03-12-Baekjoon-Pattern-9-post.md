---

layout: post

title: 2438. 별찍기

categories: [pattern]

---

[백준 2438번 문제보러가기](https://www.acmicpc.net/problem/2438)

```cpp
#include<iostream>
using namespace std;

int main() {
	int t;
	cin >> t;

	for (int i = 0; i < t; i++) {
		for (int j = 0; j <= i; j++) {
			printf("*");
		}
		printf("\n");
	}
}
```

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}