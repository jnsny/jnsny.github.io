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

### 참고
[동빈나 - C언어 기초 프로그래밍 강좌](https://www.youtube.com/watch?v=dh4hdtZ00EU&list=PLRx0vPvlEmdDNHeulKC6JM25MmZVS_3nT&index=1&t=2s)