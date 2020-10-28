---
title:  "변수 & 상수"
excerpt: ""

categories:
  - Blog
tags:
  - Blog
---

1. 변수 & 상수 개념
2. sizeof() 함수
3. Primitive 변수
4. Overflow 개념
5. 사칙연산

<br/><br/>

# 📌변수 & 상수 개념
---------------------------------------
![ob_3f1d87_c-variables-constants](https://user-images.githubusercontent.com/68745073/97417775-6a348300-194b-11eb-906b-f4ca85dcd204.jpg)
- 변수
  - 값들을 저장하는 공간
  - 변할 수 있다.
- 상수
  - 변할 수 없다.

<br/><br/>

# 📌sizeof() 함수
---------------------------------------

```c
#include <stdio.h>

int main(void)
{
	int x;
	x = 5;
	printf("변수 x의 메모리 크기는 %d입니다.", sizeof(x));	// int형 메모리 크기 = 4byte 
	return 0;
 } 
```  

<br/><br/>

# 📌Primitive 변수
---------------------------------------

```c
#include <stdio.h>

int main(void)
{
	int x = 50;
	float y = 123456789.123456789;		
	double z = 123456789.123456789;		
	
	printf("x = %d\n", x);      // int형  메모리 크기 = 4byte 
	printf("y = %.2f\n", y);    // float형  메모리 크기 = 4byte 
	printf("y = %.2f\n", z);    // double형  메모리 크기 = 8byte 
	return 0;
}
```

- 정수: int
- 실수: float, double 

```c
#include <stdio.h>

int main(void)
{
	// Ascii Code
	int x = 65;
	char y = 'A';
	char z = 'B';
	printf("%c\n", x);
	printf("%c\n", y);
	printf("%d\n", z);
	return 0;
}
```

- 문자형: char
- Ascii (American Standard Code for Information Interchange)
    - 알파벳을 사용하는 대표적인 문자 인코딩  
        (* encoding: 사용자가 입력한 문자나 기호를 컴퓨터가 이용할 수 있는 신호로 만드는 것)

<br/><br/>

# 📌Overflow 개념
---------------------------------------
```c
#include <stdio.h>
#include <limits.h>

int main(void)
{
	// INT_MAX: C에서 제공하는 int형이 가질 수 있는 최고로 큰 값
	int x = INT_MAX;	
	printf("int형의 최댓값 x는 %d입니다.\n", x);
	
	// int형이 가질 수 있는 최솟값이 출력됨, 한바퀴를 돔 => Overflow
	printf("x + 1은 %d입니다.\n", x + 1);	
	return 0;
}
```

<br/><br/>

# 📌사칙연산
---------------------------------------
```c
#include <stdio.h>

int main(void)
{
	int x = 10;
	int y = 20;
	printf("x = %d입니다.\n", x);
	printf("y = %d입니다.\n", y);
	printf("x + y = %d입니다.\n", x + y);
	printf("x - y = %d입니다.\n", x - y);
	printf("x * y = %d입니다.\n", x * y);
	printf("x / y = %d입니다.\n", x / y);	// 정수끼리 나눗셈 => 결과도 정수 
	return 0;
}
```

<br/><br/>

### 참고
<https://www.youtube.com/watch?v=dh4hdtZ00EU&list=PLRx0vPvlEmdDNHeulKC6JM25MmZVS_3nT&index=1&t=2s>  
<https://ko.wikipedia.org/wiki/ASCII>