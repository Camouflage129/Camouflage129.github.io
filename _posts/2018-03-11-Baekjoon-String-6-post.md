---

layout: post

title: 1152. 단어의 개수

categories: [string]

---

```cpp
#include<iostream>
#include<string>
using namespace std;

int cut_string(string input) {
	int count = 0;

	if (input.at(0) == ' ')
		count--;
	for (int i = 0; i < input.length(); i++) {
		if (input.at(i) == ' ' && i != input.length() - 1 && input.at(i + 1) != ' ') {
			count++;
		}
	}
	return ++count;
}

int main() {
	string input;
	int num = 0;

	getline(cin, input);
	if (input.length() > 1000000)
		exit(0);
	else {
		num = cut_string(input);
		printf("%d", num);
	}
}
```

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}