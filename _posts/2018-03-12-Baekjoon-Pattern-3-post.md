---

layout: post

title: 1193. 분수찾기

categories: [pattern]

---

[백준 1193번 문제보러가기](https://www.acmicpc.net/problem/1193)

==**문제풀이 힌트**==<br>
분자끼리의 합과 분모끼리의 합을 해나가는 수열을 만들어 보자.<br>
Ex) 1/1, 2/3, 4/4 ...<br>

```cpp
#include<iostream>
using namespace std;

int search_row(int input) {
	int sum = 1;
	int i = 1;
	while (sum < input) {
		i++;
		sum += i;
	}
	return i;
}

int search_num(int input) {
	int sum = 1;
	int i = 1;
	while (sum < input) {
		i++;
		sum += i;
	} 
	return sum;
}

void search_value(int input) {
	int parent = search_row(input);
	int son = 1;
	int num = search_num(input) - input;
	
	if((parent % 2) == 0) {
		for (int i = 0; i < num; i++) {
			son++;
			parent--;
		}
		printf("%d/%d\n",parent,son);
	}
	else {
		for (int i = 0; i < num; i++) {
			son++;
			parent--;
		}
		printf("%d/%d\n", son, parent);
	}
}

int main() {
	int input;

	cin >> input;

	search_value(input);
}
```

==**풀이**==<br>
분자의 값이 행의 값이 되고 분모의 값이 열의 값이 되는것을 알 수 있다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}