---
layout: post
title: 2941. 크로아티아
categories: [string]
---
[백준 2941번 문제보러가기](https://www.acmicpc.net/problem/2941)

==**문제풀이 힌트**==<br>
입력받은 String을 뒤에서부터 비교하며 패턴을 파악한다.<br>

```cpp
#include<iostream>
#include<string>
using namespace std;

int check(string input) {
	char check;
	int result = 0;

	for (int i = input.length() - 1; i >= 0; i--) {
		switch (input.at(i)) {
			case '=': {
				if (input.at(i - 1) == 'c' || input.at(i - 1) == 's') {
					result++;
					i = i - 1;
				}
				else if (input.at(i - 1) == 'z') {
					if (input.at(i - 2) == 'd') {
						result++;
						i = i - 2;
					}
					else {
						result++;
						i = i - 1;
					}
				}
				else
					result++;
				break;
			}
			case '-': {
				if (input.at(i - 1) == 'c' || input.at(i - 1) == 'd') {
					result++;
					i = i - 1;
				}
				else
					result++;
				break;
			}
			case 'j': {
				if (input.at(i - 1) == 'l' || input.at(i - 1) == 'n') {
					result++;
					i = i - 1;
				}
				else
					result++;
				break;
			}
			default: {
				result++;
				break;
			}
		}
	}
	return result;
}

int main() {
	string input;
	int num = 0;

	cin >> input;
	if (input.length() > 100)
		exit(0);
	else {
		num = check(input);
		printf("%d", num);
	}
}
```

**==풀이==**<br>
뒤에서 부터 비교할 경우 3가지의 경우로 나뉘어진다.<br>
=, -, j의 경우이고 다시 세분화시켜 비교하여 파악하면 된다.<br>
{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}