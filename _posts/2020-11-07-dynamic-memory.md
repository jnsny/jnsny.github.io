---
title:  "동적 메모리"
excerpt: ""

categories:
  - Blog
tags:
  - Blog
---

<br/><br/>

# 동적 메모리
---
- 메모리의 유연한 관리
- **동적 메모리 할당**이란 프로그램이 실행 도중에 동적으로 메모리를 할당 받는 것
- 필요한만큼의 메모리를 시스템으로부터 할당 받아 사용하고 사용이 끝나면 시스템에 메모리를 반납
- 동적 메모리의 사용이 끝나면 반드시 해당 메모리 영역을 명시적으로 반납해야한다.
- malloc() 계열의 라이브러리 함수를 사용하여 할당 받아 사용할 수 있다.

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	// pi => Pointer Integer
	int *pi;
	
	/*
	 malloc(a) => a 크기만큼의 메모리를 할당하라
	 sizeof(int) => int형 크기 (4byte)
	 int * => integer pointer로 형 변환 
	*/
	pi = (int *)malloc(sizeof(int));
	
	if(pi == NULL) {
		printf("동적 메모리 할당에 실패했습니다.\n");
		exit(1);	// 프로그램 자체를 종료 
	}
	
	// pi 변수에 저장된 주소가 가리키는 곳에 100이란 값을 할당 
	*pi = 100;
	printf("%d\n", *pi);
	
	/*
	 동적 메모리 사용한 이후에 무조건 해당 메모리를 반환
	 현재 할당된 4byte만큼의 메모리를 할당 해제해준다. 
	*/
	free(pi); 
	
	return 0;
}
```
![동적](https://user-images.githubusercontent.com/68745073/98435954-8a69fc00-211a-11eb-9a37-cfd8ad145285.png)
![이름 없는 노트북-11](https://user-images.githubusercontent.com/68745073/98438609-cad37500-212e-11eb-9289-76f8addaa5ed.jpg)

<br/><br/>

### 동적 메모리를 활용한 알파벳 출력
---

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	char *pc = NULL;
	int i = 0;
	
	// size of char: 1byte
	// 글자가 100개 들어갈 수 있는 메모리 공간 할당 
	pc = (char *)malloc(100 * sizeof(char));
	if(pc == NULL) {
		printf("동적 메모리 할당에 실패했습니다.\n");
		exit(1);
	}
	
	// pc가 가르키는 포인터를 1씩 증가시키며 알파벳 소문자 삽입
	// 아스키 코드에서 'a'은 97
	for(i = 0; i < 26; i++) {
		*(pc + i) = 'a' + i;
	}
	
	// 아스키 코드에서 0은 NULL을 의미
	*(pc + i) = 0;
	
	printf("%s\n", pc);
	free(pc); 
	
	return 0;
} 
```
![동적1](https://user-images.githubusercontent.com/68745073/98435955-8b029280-211a-11eb-996b-7b2584148140.png)
![이름 없는 노트북-12](https://user-images.githubusercontent.com/68745073/98435990-cef59780-211a-11eb-97a1-c98e872b4465.jpg)

<br/><br/>

### 동적 메모리를 활용한 5개의 정수 처리
---

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	int *pi, i;
	pi = (int *)malloc(5 * sizeof(int));
	if(pi == NULL) {
		printf("동적 메모리 할당에 실패했습니다.");
		exit(1);
	}
	
	pi[0] = 100;
	pi[1] = 200;
	pi[2] = 300;
	pi[3] = 400;
	pi[4] = 500;
	
	for(i = 0; i < 5; i++) {
		printf("%d\n", *(pi + i));
	}
	free(pi);
	
	return 0;
} 
```
![동적3](https://user-images.githubusercontent.com/68745073/98435956-8c33bf80-211a-11eb-9dca-ec8763e8a64d.png)

<br/><br/>

### 동적 메모리를 활용한 구조체
---

```c
#include <stdio.h>
#include <stdlib.h>

struct Book
{
	int number;
	char title[100];	
};

void showBooks(struct Book *p, int n)
{
	int i;
	for(i = 0; i < n; i++) {
		printf("번호 %d: %s\n", (p + i)->number, (p + i)->title);
	}
}

int main(void)
{
	struct Book *p;
	p = (struct Book *)malloc(2 * sizeof(struct Book));
	
	if(p == NULL) {
		printf("동적 메모리 할당에 실패했습니다.\n");
		exit(1);
	}
	
	/*
	 구조체 변수의 요소에 접근하는 일반적인 방법 => p.number
	 구조체 포인터 변수의 요소에 접근하는 방법 => p->number
	*/
	p->number = 1;
	strcpy(p->title, "C Programming");
	
	(p + 1)->number = 2;
	strcpy((p + 1)->title, "Data Structure");
	
	showBooks(p, 2);
	free(p);
	return 0; 
}
```
![동적메모리_구조체](https://user-images.githubusercontent.com/68745073/98438618-f0f91500-212e-11eb-8666-b3dc2ee21150.png)

<br/><br/>

### 동적 메모리를 활용한 2차원 배열
---

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	int i, x, y;
	
	// 2차원 배열 할당 
	int** pptr = (int**)malloc(8 * sizeof(int*));
	for(i = 0; i < 8; i++) {
		*(pptr + i) = (int *)malloc(6 * sizeof(int*));
	}
	
	// 2차원 배열 초기화 
	for(y = 0; y < 8; y++) {
		for(x = 0; x < 6; x++) {
			*(*(pptr + y) + x) = 6 * y + x;
		}
	}
	
	// 출력
	for(y = 0; y < 8; y++) {
		for(x = 0; x < 6; x++) {
			printf("%3d", *(*(pptr + y) + x));
		}
		printf("\n");
	}
	
	// 해제 
	for(y = 0; y < 8; y++){
		free(*(pptr + y));
	}
	
	return 0;
}
```
![동적메모리_2차원배열](https://user-images.githubusercontent.com/68745073/98438470-cfe3f480-212d-11eb-9ca3-d3fcf7c2b3ae.png)
![2차원배열](https://user-images.githubusercontent.com/68745073/98439782-813b5800-2137-11eb-83de-d66b2278d2fc.jpg)

<br/><br/>

### 참고
[동빈나 - C언어 기초 프로그래밍 강좌](https://www.youtube.com/watch?v=dh4hdtZ00EU&list=PLRx0vPvlEmdDNHeulKC6JM25MmZVS_3nT&index=1&t=2s)