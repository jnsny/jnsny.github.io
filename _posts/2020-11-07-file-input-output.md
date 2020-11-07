---
title:  "파일 입출력"
excerpt: ""

categories:
  - Blog
tags:
  - Blog
---

<br/><br/>

# 파일 쓰기
---

```c
#include <stdio.h>

int main(void)
{
	FILE *fp = NULL;
	// w -> 쓰기모드, r -> 읽기모드 
	fp = fopen("output.txt", "w");
	
	if(fp == NULL) {
		printf("파일 열기에 실패했습니다.\n");
	} else {
		printf("파일 열기에 성공했습니다.\n");
	}
	
	fputc('H', fp);
	fputc('E', fp);
	fputc('L', fp);
	fputc('L', fp);
	fputc('O', fp);
	fclose(fp);
	
	return 0;
}
```
![write](https://user-images.githubusercontent.com/68745073/98430759-2122c280-20f3-11eb-8295-dda0b60ade0b.png)

<br/><br/>

# 파일 읽기
---

```c
#include <stdio.h>

int main(void)
{
	FILE *fp = NULL;
	int c;
	
	// 해당 프로그램 경로에 input.txt 파일이 존재해야함 
	fp = fopen("input.txt", "r");
	
	if(fp == NULL) {
		printf("파일 열기에 실패했습니다.\n");
	} else {
		printf("파일 열기에 성공했습니다.\n");
	}
	
	// input.txt에 저장돼있는 글자 하나를 c에 할당
	// 그 글자가 파일의 끝 글자가 아니라면 반복문 진행 (EOF = End Of File)
	while((c = fgetc(fp)) != EOF) {
		 putchar(c);
	}
	fclose(fp);
	
	return 0;
}
```
![input](https://user-images.githubusercontent.com/68745073/98430761-22ec8600-20f3-11eb-9ac2-88478c464d31.png)
![read](https://user-images.githubusercontent.com/68745073/98430760-2253ef80-20f3-11eb-89e6-9c16faca2041.png)

<br/><br/>

# 파일 분석
---

```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	FILE *fp;
	char fname[256];
	char buffer[256];
	char word[256];
	int line = 0;
	
	printf("파일 이름을 입력하세요: ");
	scanf("%s", fname);
	
	printf("탐색할 단어를 입력하세요: ");
	scanf("%s", word);
	
	if( (fp = fopen(fname, "r")) == NULL ) {
		// fprintf: 파일 관련 에러 출력 시 사용 
		// stderr = standard error 
		fprintf(stderr, "파일 %s를 열 수 없습니다.\n", fname);
		return 0;
	} 
	
	/* 
	 fgets: 파일로부터 문자열을 가지고오는 함수
	 	parameter 1: 파일로부터 가져온 문자열을 할당 받는 변수
	  	parameter 2: 한번에 가지고올 문자열의 길이를 할당 받는 변수
		parameter 3: 파일 포인터 변수 
	*/
	while(fgets(buffer, 256, fp)) {
		line++;
		
		// strstr: word가 buffer에 포함돼있는지 여부를 묻는 함수 
		if(strstr(buffer, word)) {
			printf("line %d: 단어 %s이(가) 발견되었습니다.\n", line, word);
		}
	}
	fclose(fp);
	
	return 0;
}
```
![fileAnalysis](https://user-images.githubusercontent.com/68745073/98430762-241db300-20f3-11eb-9449-4e96080e33c3.png)

<br/><br/>

### 참고
[동빈나 - C언어 기초 프로그래밍 강좌](https://www.youtube.com/watch?v=dh4hdtZ00EU&list=PLRx0vPvlEmdDNHeulKC6JM25MmZVS_3nT&index=1&t=2s)