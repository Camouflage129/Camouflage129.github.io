---
layout: post
title: 2751. Merge Sort / Heap Sort
categories: [sort]
---
[백준 2751번 문제보러가기](https://www.acmicpc.net/problem/2751)

**== Merge Sort ==**

필자는 시간초과를 해결하지 못했습니다. ㅠㅠ

![Merge Sort]({{ BASE_PATH }}images\sort\Merge Sort.gif)

```c
#pragma warning (disable:4996)
#include<stdio.h>
#include<stdlib.h>

void merge(int *arr, int *tmp, int s1, int e1, int s2, int e2) {
	int index = s1;
	while (s1 <= e1 && s2 <= e2) {
		if (arr[s1] > arr[s2]) {
			tmp[index++] = arr[s2++];
		}
		else {
			tmp[index++] = arr[s1++];
		}
	}

	if (s2 > e2) {
		while (index <= e2) {
			tmp[index++] = arr[s1++];
		}
	}
	else {
		while (index <= e2) {
			tmp[index++] = arr[s2++];
		}
	}

	for (int i = s1; i <= e2; i++) {
		arr[i] = tmp[i];
	}
}

void merge_sort(int *arr, int *tmp, int start, int end) {
	int mid = (start + end) / 2;
	if (start < end) {
		merge_sort(arr, tmp, start, mid);
		merge_sort(arr, tmp, mid + 1, end);
		merge(arr, tmp, start, mid, mid + 1, end);
	}
}

int main() {
	int t;
	scanf("%d", &t);

	int *arr = (int *)malloc(sizeof(int)*t);
	int *tmp = (int *)malloc(sizeof(int)*t);
	for (int i = 0; i < t; i++) {
		scanf("%d", &arr[i]);
	}
	merge_sort(arr, tmp, 0, t-1);

	for (int i = 0; i < t; i++) {
		printf("%d\n", tmp[i]);
	}
}
```



**== Heap Sort ==**

![Heap Sort]({{ BASE_PATH }}images\sort\Heap Sort.gif)

*이미지 출처 : 위키피디아*

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}