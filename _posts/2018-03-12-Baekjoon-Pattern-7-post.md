---

layout: post

title: 2775. 부녀회장이 될테야

categories: [pattern]

---

[백준 2275번 문제보러가기](https://www.acmicpc.net/problem/2275)

==**문제풀이 힌트**==<br>
.<br>

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
.<br>
{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}