---

layout: post

title: 1316. 그룹 단어 체커

categories: [string]

---
[백준 1316번 문제보러가기](https://www.acmicpc.net/problem/1316)

==**문제풀이 힌트**==<br>
입력받은 String의 알파벳이 연속해서 나와야만 하는 것을 파악한다.<br>

```cpp
#include<iostream>
#include<string>
#include<vector>
using namespace std;

bool check_char(char check, string input, int num) {
	for (int i = 0; i < input.length(); i++) {
		if (check == input[i] && abs(num - i) <= 1)
			num = i;
		else if (check == input[i] && abs(num - i) > 1) {
			for (int j = i; j < num; j++) {
				if(input[j] != check)
					return false;
			}
		}
	}
	return true;
}


int main() {
	int size;
	vector<string> vector;
	string input;
	char check;
	bool result;
	int count = 0;

	cin >> size;
	if (size > 100)
		exit(0);
	else {
		vector.reserve(size);
		for (int i = 0; i < size; i++) {
			cin >> input;
			if (input.length() > 100)
				exit(0);
			else
				vector.push_back(input);
		}

		for (int i = 0; i < vector.size(); i++) {
			for (int j = 0; j < vector[i].length(); j++) {
				check = vector[i].at(j);
				result = check_char(check, vector[i], j);
				if (result == false)
					break;
			}
			if(result == true)
				count++;
		}
		printf("%d", count);
	}
}
```

**==풀이==**<br>
필자의 경우 프로그램이 다음과 같이 구성된다.<br>
1. 입력받은 스트링에서 각 알파벳이 연속되서 나타나는지 체크하는 함수<br>
2. 입력받은 함수가 그룹 단어일 때, 개수를 Count<br>
알파벳이 연속되서 나타는지는 at(자바의 경우charAt)으로 <br>
해당 배열의 인덱스와 값을 넘겨서 입력받은 String 전체와 비교하여 판별한다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}