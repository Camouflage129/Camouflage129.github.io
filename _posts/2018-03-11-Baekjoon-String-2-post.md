---

layout: post

title: 10809 알파벳 찾기

categories: [string]

---

```cpp
#include<iostream>
#include<string>
using namespace std;

void func(char code, char x, int code_num, int ap_num, int ap[]) {
	if (code == x && ap[ap_num] == -1)
		ap[ap_num] = code_num;
	else {
		if (ap_num != 26)
			func(code, ++x, code_num, ++ap_num, ap);
	}
}

int main() {
	string input;
	char code;
	int ap[26];

	for (int i = 0; i < 26; i++) {
		ap[i] = -1;
	}

	cin >> input;

	for (int i = 0; i < input.length(); i++) {
		code = input.at(i);
		func(code, 'a', i, 0, ap);
	}

	for (int i = 0; i < 26; i++) {
		printf("%d ", ap[i]);
	}
}
```

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}