---
title:  "환경설정 & Hello World 출력"
excerpt: ""

categories:
  - Blog
tags:
  - Blog
---

<br/><br/>

# 📌Dev-C++ 다운로드
---------------------------------------

<!-- 링크 표시법 : [Title](link) -->
1. [Dev-C++ 다운로드 페이지 링크](https://sourceforge.net/projects/orwelldevcpp/)  
2. 초기화면  
![compiler](https://user-images.githubusercontent.com/68745073/97412166-897be200-1944-11eb-8c3e-7ae7cafd7758.png)  

<br/><br/><br/><br/>

# 📌Hello World 출력
---------------------------------------
- 소스작성 

```c
#include <stdio.h>	// 라이브러리를 추가하는 부분

int main(void)	// main 함수는 가장 첫번째로 실행됨 
{
	printf("Hello World!");
	return 0;
}
```  

<br/><br/>

- 파일저장  
  - 확장자를 .c 타입으로 저장한다.
![fileType](https://user-images.githubusercontent.com/68745073/97413299-f5ab1580-1945-11eb-81c5-d428e381cfe1.png)  

<br/><br/>

- 컴파일 & 런  
  - F11 키를 누르거나, 아래 이미지의 아이콘을 클릭한다.
![icon](https://user-images.githubusercontent.com/68745073/97413983-c517ab80-1946-11eb-9c21-ca29c81cad1e.png) 

<br/><br/>

- 출력화면  
![hello](https://user-images.githubusercontent.com/68745073/97411437-9fd56e00-1943-11eb-9852-bb7735cd4a20.png)  

<br/><br/>

### 참고
[동빈나 - C언어 기초 프로그래밍 강좌](https://www.youtube.com/watch?v=dh4hdtZ00EU&list=PLRx0vPvlEmdDNHeulKC6JM25MmZVS_3nT&index=1&t=2s)