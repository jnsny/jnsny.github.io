---
title:  "조건문 & 반복문"
excerpt: ""

categories:
  - Blog
tags:
  - Blog
---

<br/><br/>

# 📌조건문
---------------------------------------

```c
#include <stdio.h>

int main(void)
{
	int score = 85;
	
	if (score >= 90) {
		printf("당신의 학점은 A입니다. \n");
	} else if (score >= 80) {
		printf("당신의 학점은 B입니다. \n");    // 출력
	} else if (score >= 70) {
		printf("당신의 학점은 C입니다. \n");
	} else {
		printf("당신의 학점은 F입니다. \n");
	}
	
	return 0;
}
``` 

<br/><br/>

### ✅ 윤년판독
---------------------------------------

```c
#include <stdio.h>

int main(void)
{
	/*
		윤년 => 4년마다, 그렇지만 100년 단위일 때는 윤년에 해당하지 않도록 설정
		윤년 => 400년 단위일 때는 어떤 상황이든간에 윤년으로 설정 
	*/
	
	int year = 2020;
	if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
		printf("%d년은 윤년입니다.\n", year);
	} else {
		printf("%d년은 윤년이 아닙니다.\n", year);
	}
	
	return 0; 
}
```

<br/><br/><br/><br/>

# 📌반복문
---------------------------------------

```c
#include <stdio.h>

int main(void)
{
	int i = 1, sum = 0;
	while(i <= 1000) {
		sum = sum + i;
		i++;		
	}
	printf("1부터 1000까지의 합은 %d입니다.", sum);
	return 0;
}
```

<br/><br/>

### ✅ 사각형 출력
---------------------------------------

```c
#include <stdio.h> 
#define N 10

int main(void)
{
	int i, j;
	// 총 N번 반복 
	for (i = 0; i < N; i++) {	// 초기화; 조건문; 반복하면서 연산
		for (j = 0; j < N; j++) {
			printf("★");
		}
		printf("\n");
	}
	
	return 0;
}
```

* 출력결과  
![사각형출력](https://user-images.githubusercontent.com/68745073/97780214-9e67a800-1bc6-11eb-8193-77d523b024f9.png)

<br/><br/>

### ✅ 피라미드 출력
---------------------------------------

```c
#include <stdio.h>
#define N 20

int main(void)
{
	int i, j;
	for (i = 0; i < N; i++) {
		// 공백 만들기 
		for (j = N - i - 1; j > 0; j--) {
			printf("  ");
		}
		
		// 왼쪽별 출력 
		for (j = 0; j < i; j++) {
			printf("★");
		}
		
		// 오른쪽별 출력 
		for (j = 0; j < i - 1; j++) {
			printf("★");
		}
		
		printf("\n");
	}
	
	return 0;
}
```

* 출력결과  
![피라미드출력](https://user-images.githubusercontent.com/68745073/97780215-9f98d500-1bc6-11eb-87d0-dcd5753077c8.png)

<br/><br/>

### 참고
[동빈나 - C언어 기초 프로그래밍 강좌](https://www.youtube.com/watch?v=dh4hdtZ00EU&list=PLRx0vPvlEmdDNHeulKC6JM25MmZVS_3nT&index=1&t=2s)