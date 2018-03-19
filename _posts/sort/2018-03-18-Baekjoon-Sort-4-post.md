---
layout: post
title: 10989. Counting Sort / Radix Sort
categories: [sort]
---
[백준 10989번 문제보러가기](https://www.acmicpc.net/problem/10989)

**== Counting Sort ==**

필자는 메모리 문제(런타임 에러)를 해결하지 못했습니다.

![Counting Sort]({{ BASE_PATH }}images\sort\Counting Sort.gif)

```c
#pragma warning (disable:4996)
#include<stdio.h>
#include<stdlib.h>

int main() {
	int input[10001] = { -1 };
	int count[10001] = { 0 };
	int cumulative[10001] = { -1 };

	int t;
	scanf("%d", &t);

	for (int i = 1; i <= t; i++) {
		scanf("%d", &input[i]);
		count[input[i]]++;
	}

	int sum = 0;
	for (int i = 1; i <= 10000; i++) {
		if (count[i] != 0) {
			sum += count[i];
			cumulative[i] = sum;
		}
	}

	int *result = (int*)malloc(sizeof(int)*(sum+1));
	for (int i = 1; i <= 10000 ; i++) {
		if (input[i] > 0) 
			result[cumulative[input[i]]--] = input[i];
	}

	for (int i = 1; i <= sum; i++) {
		printf("%d\n",result[i]);
	}
}
```



**== Radix Sort ==**

![Radix Sort]({{ BASE_PATH }}images\sort\Radix Sort.png)



*이미지 출처 : 위키피디아*

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}