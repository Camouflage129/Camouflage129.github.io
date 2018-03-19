---
layout: post
title: 2750. Bubble Sort / Insertion Sort
categories: [sort]
---
[백준 2750번 문제보러가기](https://www.acmicpc.net/problem/2750)

**== Bubble Sort ==**

하나씩 비교하며 가장 큰수를 맨 뒤로 두는 정렬방법<br><img src="{{ BASE_PATH }}images\sort\Bubble Sort.gif" alt="Bubble Sort"/>

```c
#pragma warning (disable:4996)
#include<stdio.h>
#include<stdlib.h>

void bubble_sort(int *arr, int size) {
	int temp = arr[0];
	for (int i = 0; i < size; i++) {
		for (int j = 0; j < size - i - 1; j++) {
			if (arr[j] > arr[j + 1]) {
				temp = arr[j + 1];
				arr[j + 1] = arr[j];
				arr[j] = temp;
			}
		}
	}
}

int main() {
	int t, input;
	scanf("%d", &t);

	int *arr = (int *)malloc(sizeof(int)*t);
	for (int i = 0; i < t; i++) {
		scanf("%d", &arr[i]);
	}
	bubble_sort(arr, t);

	for (int i = 0; i < t; i++) {
		printf("%d\n", arr[i]);
	}
}
```



**== Insertion Sort ==**

2번째 인덱스 부터 자신보다 앞에있는 숫자와 비교하는 정렬방법

![Insertion Sort]({{ BASE_PATH }}images\sort\Insertion Sort.gif)

```c
#pragma warning (disable:4996)
#include<stdio.h>
#include<stdlib.h>

void insertion_sort(int *arr, int size) {
	for (int i = 1; i < size; i++) {
		for (int j = 0; j < i; j++) {
			int temp;
			if (arr[j] > arr[i]) {
				temp = arr[j];
				arr[j] = arr[i];
				arr[i] = temp;
			}
		}
	}
}

int main() {
	int t, input;
	scanf("%d", &t);

	int *arr = (int *)malloc(sizeof(int)*t);
	for (int i = 0; i < t; i++) {
		scanf("%d", &arr[i]);
	}
	insertion_sort(arr, t);

	for (int i = 0; i < t; i++) {
		printf("%d\n", arr[i]);
	}
}
```

*이미지 출처 : 위키피디아*

{% if site.dispus-shortname %}{% include dispus.html %}{% endif %}