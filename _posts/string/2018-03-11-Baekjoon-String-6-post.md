---

layout: post

title: 1157. 단어 공부

categories: [string]

---

[백준 1157번 문제보러가기](https://www.acmicpc.net/problem/1157)


```cpp
#include<iostream>
#include<string>
using namespace std;

void func(char code, char x, char y, int i, int ap[]) {
	if (code == x || code == y)
		ap[i]++;
	else
		func(code, ++x, ++y, ++i, ap);
}

int func2(int ap[]) {
	int i, max = 0, count = 0;
	//max값 뽑아내기
	for (i = 0; i < 26; i++) {
		if (max < ap[i])
			max = ap[i];
	}
	//가장 높은 알파벳 번호 찾기
	for (i = 0; i < 26; i++) {
		if (max == ap[i])
			break;
	}
	//중복체크
	for (int j = 0; j < 26; j++) {
		if (max == ap[j])
			count++;
	}

	if (count >= 2)
		return -1;
	else
		return i;
}


int main() {
	string input;
	char code;
	int ap[26] = { 0 };
	char result;

	cin >> input;

	for (int i = 0; i < input.length(); i++) {
		code = input.at(i);
		func(code, 'a', 'A', 0, ap);
	}

	if (func2(ap) == -1)
		result = '?';
	else
		result = func2(ap) + 65;

	printf("%c", result);
}
```

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}