---

layout: post

title: 2908. 상수

categories: [string]

---

```cpp
#include<iostream>
#include<string>
using namespace std;

int change(int x) {
	string change = to_string(x);
	string temp = change;
	for (int i = 0; i < change.length(); i++) {
		temp[change.length() - (i + 1)] = change[i];
	}
	return atoi(temp.c_str()); // string -> int 변환함수
}

int main() {
	int x, y;

	cin >> x;
	cin >> y;

	x = change(x);
	y = change(y);

	(x > y) ? printf("%d\n", x) : printf("%d\n", y);
}
```

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}