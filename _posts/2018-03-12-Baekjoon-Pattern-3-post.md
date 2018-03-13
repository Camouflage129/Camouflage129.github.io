---

layout: post

title: 2775. 부녀회장이 될테야

categories: [pattern]

---

[백준 2775번 문제보러가기](https://www.acmicpc.net/problem/2775)

==**문제풀이 힌트**==<br>
0층에는 1호에 1명 2호에 2명 ... 이 있고<br>
K층에 N명이라면, 그 전 층까지의 합이 계속해서 쌓인다는 것을 파악 한다.<br>

```cpp
#include<iostream>
using namespace std;

int zeroFloor(int roomNumber) {
	int result = 0;
	for(int i=1; i<=roomNumber; i++) {
		result += i;
	}
	return result;
}

int cal(int floor, int roomNumber) {
	int result = 0;
	if (floor != 1) {
		int cal_floor = floor - 1;
		for (int i = 1; i <= roomNumber; i++) {
			result += cal(cal_floor, i);
		}
	}
	else if (floor == 0)
		return roomNumber;
	else {
		result += zeroFloor(roomNumber);
	}
	return result;
}

int main() {
	int floor, roomNumber;
	int t;
	cin >> t;
	for (int i = 0; i < t; i++) {
		cin >> floor;
		cin >> roomNumber;

		printf("%d\n", cal(floor, roomNumber));
	}
}
```

**==풀이==**<br>
2층의 3호를 예로 들자.<br>
0층의 1호~3호까지의 합 + 1층의 1호~3호까지의 합이다<br>
= 0:1~3 + 0:1 + 0:1~2 + 0:1~3 임을 알 수있다.<br>
패턴 파악이 끝났으니 잘 만들도록 한다.<br>
{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}