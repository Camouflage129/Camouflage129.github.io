---

layout: post

title: 1193. 분수찾기

categories: [pattern]

---

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

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}