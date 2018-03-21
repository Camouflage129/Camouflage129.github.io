---
layout: post
title: 2108. 통계학
categories: [sort]
---
[백준 2108번 문제보러가기](https://www.acmicpc.net/problem/2108)

**== 문제풀이 힌트 ==**<br>

최빈값 외에는 어려운 것이 없다.<br>

최빈값을 구할 때, 반복수를 줄이기위해 int형이 두개인 클래스를 만들어서 쓰도록 하자.<br>

```c
#pragma warning (disable:4996)
#include<iostream>
#include<algorithm>
#include<vector>
#include<math.h>
using namespace std;

class Count {
public:
	int num;
	int count;
	Count(int input_num, int input_count) {
		num = input_num;
		count = input_count;
	}

	bool operator<(const Count &t) const {
		return (count < t.count);
	}
};

int main() {
	int t;
	scanf("%d", &t);

	int *arr = new int[t];
	double sum = 0;

	for (int i = 0; i < t; i++) {
		scanf("%d", &arr[i]);
		sum += arr[i];
	}
	sort(arr, arr + t);

	vector<Count> vcount;
	int index = 0;
	vcount.push_back(Count(arr[0], 1));
	for (int i = 1; i < t; i++) {
		if (vcount[index].num == arr[i])
			vcount[index].count++;
		else {
			vcount.push_back(Count(arr[i], 1));
			index++;
		}
	}
	sort(vcount.begin(), vcount.end());

	vector<int> result;
	printf("%.0lf\n", round(sum / t));
	printf("%d\n", arr[t / 2]);
	if (vcount.size() >= 2) {
		for (int i = vcount.size() -1; i >= 0 ; i--) {
			if (vcount[vcount.size() - 1].count == vcount[i].count) {
				result.push_back(vcount[i].num);
			}
		}
		if(result.size() == 1) 
			printf("%d\n", vcount[vcount.size() - 1].num);
		else {
			sort(result.begin(), result.end());
			printf("%d\n",result[1]);
		}
	}
	else
		printf("%d\n", vcount[0].num);
	printf("%d\n", arr[t - 1] - arr[0]);
}
```



**== 풀이 ==**<br>

최빈값을 구한 알고리즘은 다음과 같다.<br>

1 1 2 2 2 3 4 일 때, 값을 가지고있는 num, 그 값의 개수를 셀 count 변수가 있는 클래스를 만든다.<br>

이 후, 벡터로 이뤄진 vcount[0]에 입력 후 정렬된 배열의 첫 값을 넣고 count를 1을 넣어준다.<br>

이제 위의 입력 배열의 2번째 값과 비교하면서 같으면 vcount num이 1이므로 1의 개수를 세주기 위해<br>

count를 증가시켜주면 되고 3번째 값과는 다르므로 그때는 다시 vector에 넣으면서 카운트를 1세주고<br>

다시 그 뒤의 값과 비교하면서 진행하게 하면 입력된 숫자마다 각 카운트의 개수를 O(n)으로 셀 수 있다.<br>

이제 출력시에는 ''최빈 값 중" 에서 2번째로 작은 값에 주목해야한다.<br>

결국, 최고 카운트 수가 같은 수들이 있을 수 있으므로 벡터에 그 값들을 넣은 후 정렬하여 출력해주도록 한다.<br>

이 때, result는 자기 자신도 넣으므로 무조건 사이즈가 1이상이다.<br>

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}