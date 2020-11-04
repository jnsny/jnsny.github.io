---
title:  "C언어 & 사용자 정의 함수"
excerpt: ""

categories:
  - Blog
tags:
  - Blog
---

<br/><br/>

# 📌C언어
---------------------------------------
- 고급언어에 속하면서도 거의 어셈블리어 취급을 받는다.  
  (* 어셈블리어: 기계어와 일대일 대응이 되는 컴퓨터 프로그래밍의 저급 언어)
- **사용자 정의 함수 / 배열 / 문자열 / 포인터**가 중요하다.
- 메모리 주소에 직접 접근할 수 있다는 점이 강력한 장점이고 다양한 운영체제 및 언어들의 기본이 된다.  
  (* 특히 유닉스라는 운영체제는 C언어로 만들어졌다.)

<br/><br/>

# 📌사용자 정의 함수

<br/><br/>

### ✅ 시간 더하기
---------------------------------------

```c
#include <stdio.h>

// 전역변수: 프로그램 전체에서 접근 가능한 변수
int hour;
int minute;
int minuteAdd;

void counter()
{
	minute += minuteAdd;
	hour += minute / 60;
	minute %= 60;	// 몫은 시간, 나머지는 분 
	hour %= 24;		// 몫은 일수, 나머지는 시 
} 

int main(void)
{
	printf("시를 입력하세요: ");
	scanf("%d", &hour);
	printf("분을 입력하세요: ");
	scanf("%d", &minute);
	printf("더할 분을 입력하세요: ");
	scanf("%d", &minuteAdd);
	counter();
	printf("더해진 시간은 %d시 %d분 입니다.\n", hour, minute);
	 
	return 0;
}
``` 

<br/><br/>

### ✅ 거스름돈
---------------------------------------

```c
#include <stdio.h> 

// 특정한 금액을 받아서 가장 적은 거스름 화폐의 개수 구하기 
int smallest(int number)
{
	int count = 0;
	
	while(number >= 50000) {
		number -= 50000;
		count++;
	}
	
	while(number >= 10000) {
		number -= 10000;
		count++;
	}
	
	while(number >= 5000) {
		number -= 5000;
		count++;
	}
	
	while(number >= 1000) {
		number -= 1000;
		count++;
	}
	
	while(number >= 500) {
		number -= 500;
		count++;
	}
	
	while(number >= 100) {
		number -= 100;
		count++;
	}
	
	while(number >= 50) {
		number -= 50;
		count++;
	}
	
	while(number >= 10) {
		number -= 10;
		count++;
	}
	
	return count;
}

int main(void)
{
	int number;
	printf("금액을 입력하세요: ");
	scanf("%d", &number);
	printf("최소로 줄 수 있는 화폐의 개수는 %d개 입니다.\n", smallest(number));
	return 0;
}
``` 

<br/><br/>

### ✅ 날짜 거리 계산
---------------------------------------

```c
#include <stdio.h>

int getDays(int month, int day)
{
	int i, sum = 0;
	
	for(i = 1; i < month; i++) {
		// 이 프로그램에서는 윤년을 감안하지 않는다. 
		if(i == 2) {
			sum += 28;
		} else if(i % 2 == 0) {
			sum += 30;
		} else {
			sum += 31;
		}
	}
	
	return sum + day;
}

int main(void) {
	int month, day;
	scanf("%d, %d", &month, &day);
	printf("1월 1일부터 해당 날짜까지의 거리는 %d일 입니다.", getDays(month, day));
	
	return 0;
}
``` 

<br/><br/>

### 참고
[동빈나 - C언어 기초 프로그래밍 강좌](https://www.youtube.com/watch?v=dh4hdtZ00EU&list=PLRx0vPvlEmdDNHeulKC6JM25MmZVS_3nT&index=1&t=2s)