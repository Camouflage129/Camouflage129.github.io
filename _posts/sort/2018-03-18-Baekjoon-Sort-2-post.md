---
layout: post
title: 1472. 소트인사이드
categories: [sort]
---
[백준 1472번 문제보러가기](https://www.acmicpc.net/problem/1472)

**== 문제풀이 힌트 ==**<br>

나머지 연산을 활용하면 편하다.

```c
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;

void pushNum(long long input, vector<int>& result) {
	result.push_back(input % 10);

	if(input / 10 >= 1)
		pushNum(input / 10, result);
}

int main() {
	long long input;
	cin >> input;

	vector<int> result;
	pushNum(input, result);

	sort(result.begin(), result.end());
	for (int i = result.size() - 1; i >= 0; i--) {
		printf("%d", result[i]);
	}
}
```



**== 풀이 ==**<br>

10으로 나눈 나머지 마지막 끝값부터 vector에 넣어준후 Sort를 한다.<br>

Sort 알고리즘은 기본적으로 오름차순이므로 역으로 출력해주면 끝.<br>

주의할 점은 vector를 넘길 때, 주소를 넘겨야하므로 &를 써야한다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}