---

layout: post

title: 1924. 2007년

categories: [pattern]

---

```cpp
#include<iostream>
using namespace std;

int cal_day(int m, int d, int c_m, int c_d) {
	if (m == c_m && m != 1)
		return (c_d + d) % 7;
	else if (m == 1)
		return d % 7;
	else {
		if (c_m == 1 || c_m == 3 || c_m == 5 || c_m == 7 || c_m == 8 || c_m == 10 || c_m == 12)
			cal_day(m, d, ++c_m, c_d + 31);
		else if (c_m == 2)
			cal_day(m, d, ++c_m, c_d + 28);
		else if (c_m == 4 || c_m == 6 || c_m == 9 || c_m == 11)
			cal_day(m, d, ++c_m, c_d + 30);
	}
}

void result(int d) {
	if (d == 1)
		printf("MON\n");
	else if (d == 2)
		printf("TUE\n");
	else if (d == 3)
		printf("WED\n");
	else if (d == 4)
		printf("THR\n");
	else if (d == 5)
		printf("FRI\n");
	else if (d == 6)
		printf("SAT\n");
	else if (d == 0)
		printf("SUN\n");
	else
		printf("Error\n");
}


int main() {
	int m,d;
	cin >> m;
	cin >> d;

	result(cal_day(m, d, 1, 0));
}
```

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}