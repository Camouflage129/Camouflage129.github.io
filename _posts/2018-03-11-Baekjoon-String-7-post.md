---

layout: post

title: 2675. 문자열 반복

categories: [string]

---
[백준 2675번 문제보러가기](https://www.acmicpc.net/problem/2675)

```cpp
#include<iostream>
#include<string>
#include<vector>
using namespace std;

void printInput(vector<int> vnum, vector<string> vstring) {
	for (int i = 0; i < vnum.size(); i++) {
		for (int j = 0; j <vstring[i].length(); j++) {
			for (int k = 0; k < vnum[i]; k++) {
				printf("%c", vstring[i].at(j));
			}
		}
		printf("\n");
	}
}

int main() {
	int size;
	int input_num;
	string input_string;
	vector<int> vnum;
	vector<string> vstring;

	cin >> size;
	for (int i = 0; i < size; i++) {
		cin >> input_num;
		cin >> input_string;
		vnum.push_back(input_num);
		vstring.push_back(input_string);
	}
	printInput(vnum,vstring);
}
```

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}