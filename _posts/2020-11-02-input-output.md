---
title:  "기본 입출력"
excerpt: ""

categories:
  - Blog
tags:
  - Blog
---

<br/><br/>

# 📌기본 입출력
---------------------------------------
- getchar() 함수로 버퍼의 공백 문자를 받아낼 수 있다.
- scanf() 함수를 사용할 때 변수 이름 앞에 &(주소를 나타냄)를 붙여야 한다.
- 형식 지정자를 '%c'로 하면 엔터도 하나의 공백 문자로서 입력 받을 수 있다.

<br/><br/>

### ✅ 계산기
---------------------------------------

```c
#include <stdio.h>

int main(void)
{
	int x, i;
	printf("정수를 입력하세요: ");
	scanf("%d", &x);
	for(i = 1; i <= 9; i++) {
		printf("%d X %d = %d\n", x, i, x*i);
	}
	return 0;
}
``` 

<br/><br/>

### ✅ 정수 개수 구하기
---------------------------------------

```c
#include <stdio.h> 

int main(void)
{
	int number, x, i, sum = 0;
	
	printf("정수의 개수를 입력하세요: ");
	scanf("%d", &number);
	
	for(i = 0; i < number; i++) {
		printf("정수의 값을 입력하세요: ");
		scanf("%d", &x);
		sum += x;
	}
	printf("전체 정수의 값은 %d입니다.", sum);
	
	return 0;
}
``` 

<br/><br/>

### ✅ 구구단
---------------------------------------

```c
#include <stdio.h>

int main(void)
{
	int x, i;
	printf("정수를 입력하세요: ");
	scanf("%d", &x);
	for(i = 1; i <= 9; i++) {
		printf("%d X %d = %d\n", x, i, x*i);
	}
	return 0;
}
``` 

<br/><br/>

### 참고
[동빈나 - C언어 기초 프로그래밍 강좌](https://www.youtube.com/watch?v=dh4hdtZ00EU&list=PLRx0vPvlEmdDNHeulKC6JM25MmZVS_3nT&index=1&t=2s)