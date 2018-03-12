---

layout: post

title: 5622. 다이얼

categories: [string]

---

```cpp
#include<iostream>
#include<string>
using namespace std;

int check (char temp) {
	if ('A' <= temp && temp <= 'C')
		return 3;
	else if ('D' <= temp && temp <= 'F')
		return 4;
	else if ('G' <= temp && temp <= 'I')
		return 5;
	else if ('J' <= temp && temp <= 'L')
		return 6;
	else if ('M' <= temp && temp <= 'O')
		return 7;
	else if ('P' <= temp && temp <= 'S')
		return 8;
	else if ('T' <= temp && temp <= 'V')
		return 9;
	else if ('W' <= temp && temp <= 'Z')
		return 10;
}

int sum (string input) {
	int sum = 0;
	char temp;

	for (int i = 0; i < input.length(); i++) {
		temp = input.at(i);
		sum += check(temp);
	}
	return sum;
}

int main() {
	string input;

	cin >> input;

	printf("%d",sum(input));
}
```

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}