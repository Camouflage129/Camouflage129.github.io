---
layout: post
title: 1181. 단어 정렬
categories: [sort]
---
[백준 1181번 문제보러가기](https://www.acmicpc.net/problem/1181)

**== 문제풀이 힌트 ==**<br>

풀이 방법이 두가지가 있다.<br>

편하게 pair를 이용한 방법이 있으며, 비교함수를 만들어서 하는 방법이 있다.<br>

물론 메모리, 속도 모두 후자가 효율이 좋으므로 잘 생각해보자.<br>

```cpp
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
using namespace std;

int main() {
	int t;
	string input;
	vector<pair<int, string>> vinput;

	cin >> t;
	for (int i = 0; i < t; i++) {
		cin >> input;
		vinput.push_back(pair<int, string>(input.length(), input));
	}

	sort(vinput.begin(), vinput.end());
	for (int i = 0; i < vinput.size(); i++) {
		if (i != 0 && vinput[i].second == vinput[i - 1].second)
			continue;
		else
			cout << vinput[i].second << endl;
	}
}
```

```cpp
#include<iostream>
#include<string>
#include<algorithm>
using namespace std;

bool cmp(const string &a, const string &b) {
	if (a.length() == b.length())
		return a < b;
	return a.length() < b.length();
}

int main() {
	int t;
	string input[20000];
	
	cin >> t;
	for (int i = 0; i < t; i++) {
		cin >> input[i];
	}
	
	sort(input, input + t, cmp);
	for (int i = 0; i < t; i++) {
		if (i != 0 && input[i] == input[i - 1])
			continue;
		else
			cout << input[i] << endl;
	}
}
```

**== 풀이 ==**<br>

pair를 이용한 경우 첫번째를 기준으로 정렬 후 두번째 기준을 잡는다<br>

딱 문제에서 요구한 정렬방식을 완벽하게 따르기 때문에 사용해서 할 경우 매우 편하다.<br>

후자의 경우는 bool compare 함수를 직접 만들어주어야 하는데<br>

클래스나 struct를 쓸 경우에는 비교할 때 반드시 알아야 하기에 꼭 알아두고 넘어가자<br>

마지막으로 주의할 점은 중복된 값은 출력하지 않는 것이다.<br>

필자의 경우 처음에 바보같이 이전의 입력된 값을 모두 체크하여 중복일 경우 값을 입력받지 않았는데<br>

이렇게 하면 시간초과가 되버리므로 출력할 때, 앞에 이미 출력된 값이 있으면 출력하지 않게 하자<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}