---

layout: post

title: 1193. 분수찾기

categories: [pattern]

---

[백준 1193번 문제보러가기](https://www.acmicpc.net/problem/1193)

==**문제풀이 힌트**==<br>
행렬에 각 숫자순서를 적어보고, 대각선 형태로 짤라서 보자<br>
또한 짝수일 때, 홀수일 때의 규칙을 찾아보자.<br>

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
대각선으로 짜르게되면 짝수번째 대각선의 경우에는<br>
가장 좌측 하단으로 부터 우측 상단으로 값을 변동시키고 <br>
홀수 번째의 경우에는 가장 우측 상단부터 좌측 하단으로 값을 변동시킨다.<br>
위의 알고리즘이 핵심인 이유는 i를 증가시키며 합을 구할 때,<br>
i = 2 / sum = 3  ->  2번째 대각선 2행 좌측하단 숫자번호 3 <br>
i = 3 / sum = 6  ->  3번째 대각선 3열 우측상단 숫자번호 6 <br>
i = 4 / sum = 10  ->  4번째 대각선 4행 좌측하단 숫자번호 10 <br>
i = 5 / sum = 15  ->  5번째 대각선 5열 우측상단 숫자번호 15 <br>
의 규칙을 찾을 수 있기 때문이다.<br>
따라서 이와 같이 행과 그 번호를 구한 다음 이동시켜야 하는 만큼 <br>
분자와 분모의 값을 알맞게 변경해주면 된다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}