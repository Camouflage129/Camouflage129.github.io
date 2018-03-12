---

layout: post

title: 2292. 벌집

categories: [pattern]

---

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

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}