---
title: "2주차 Java 스터디"
category: Java
permalink: '/category/Java'
---

## 자료형

### 1. 자료형의 의미

- 저장할 수 있는 값의 형태를 지정 (자료형에 맞는 데이터를 입력해야함)
- Java 프로그램의 모든 변수/상수는 자료형 선언 후 사용가능

But.. Kotlin은 타입 추론이 가능!!



### 2. 자료형의 종류

- 기본 자료형 : boolean, byte, short, int, long, float, double, char

  기본자료형은 소문자로 시작

- 참조 자료형 : String, Array, Map, Class, Interface...

  참조 자료형은 대문자로 시작 

  

#### 메모리 영역

Java의 메모리 구조

![스크린샷 2022-07-17 오전 2.48.43](/Users/byunghoonkim/Library/Application Support/typora-user-images/스크린샷 2022-07-17 오전 2.48.43.png)

- 기본 자료형은 값을 stack 메모리 저장
- 참조자료형은 값을 heap 메로리에 저장



![스크린샷 2022-07-17 오전 2.52.12](/Users/byunghoonkim/Library/Application Support/typora-user-images/스크린샷 2022-07-17 오전 2.52.12.png)

- 모든 변수는 Stack 메모리에 저장됨.
- 기본 자료형의 경우 value가 stack 메모리에 함께 저장됨
- 참조 자료형의 경우 value가 heap 메모리에 저장됨. (stack메모리에 변수와 value의 주소값만 저장됨)



### 기본자료형

##### 필수 암기

정수.

- boolean : 1byte = 8bit (true, false) <-실제 2bit면 충분 하지만 1byte가 최소 단위.
- byte : 1byte = 8bit (-2<sup>7</sup> ~ 2<sup>7</sup> - 1)
- short : 2byte = 16bit (-2<sup>15</sup> ~2<sup>15</sup> - 1)
- Int : 4byte = 32bit (-2<sup>31</sup> ~ 2<sup>31</sup> - 1)
- long : 8byte = 64bit (-2<sup>63</sup> ~ 2<sup>63</sup> - 1)

실수.

- float : 4byte = 32bit 
- double : 8byte = 64bit

문자(정수)

- char : 2byte = 16bit (유니코드문자)

실수의 경우는 표현해하는 수의 범위가 넓기 때문에(ex. 소수) 범위가 byte의 범위보다 넓다.(외울 필요는 없음.)



### 진법 표현

- 8진수 : (ex. <span style='background-color:#fff5b1'>0</span>123) 맨앞에 0을 표기하면 8진수
- 16진수 : (ex.<span style='background-color:#fff5b1'>0x</span>123) 맨앞에 0x를 표기하면 16진수
- 2진수 : (ex.<span style='background-color:#fff5b1'>0b</span>123) 맨앞에 0b를 표기하면 2진수



#### 진법 정수 변환
정수 123 -> 1x10<sup>2</sup> + 2x10<sup>1</sup> + 3x10<sup>0</sup>
0123 -> 1x8<sup>2</sup> + 2x8<sup>1</sup> + 3x8<sup>0</sup>
0x123 -> 1x16<sup>2</sup> + 2x16 + 3x1



#### 변수에 문자 저장시 메모리

![스크린샷 2022-07-17 오후 9.43.26](/Users/byunghoonkim/Library/Application Support/typora-user-images/스크린샷 2022-07-17 오후 9.43.26.png)

메모리에는 직접적으로 문자를 넣을수 없어 유니코드값(ex. 'A' = 65)으로 저장



### 기본자료형 (Type변환)

- 리터럴 타입 : 자료형 없이 값으로 입력하는 경우 값의 형태에 따라 대표 자료형으로 자동 변환됨. (ex. 정수는 기본적으로 int로 인식, 실수값은 기본적으로 double로 인식, 문자열은 기본적으로 String으로 인식)

- 자동타입변환 : 형변환(캐스팅)을 통해 자동으로 자료형을 변환함.
  ##### long l = 3 <- 3은 리터럴타입에 의해서 int이지만 int보다 long이 자료형이 더 커서 컴파일러가 자동타입변환을 해줘 3이 long형으로 변환됨.

  ##### float c = 3.2 <- 3.2는 double형이고 c는 float이기때문에 오류 발생

![스크린샷 2022-07-17 오후 9.55.51](/Users/byunghoonkim/Library/Application Support/typora-user-images/스크린샷 2022-07-17 오후 9.55.51.png)
