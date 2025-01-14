## String 참조형

### String 클래스

- 문자열 저장 <span style="color:red">클래스</span> 타입
- 문자열은 ""안에 표기.

### String Class의 특징

- 객체내의 값 변경 <span style="color:red">불가능</span> -> 값의 변경을 위해서는 새로운 객체를 생성하여새 변경.
- 리터럴을 바로 입력한 데이터는 하나의 객체를 공유. -> 리터럴로 바로 입력시에는 새로운 객체를 생성하여 대입한다고 생각.

리터럴 대입의 경우 대입할때마다 Heap 메모리에는 새로운 객체가 저장됨.

### String 객체의 '+' 연산

- 문자열 + 문자열 -> 문자열 연결.
- 문자열 + 기본자료형 -> 기본자료형을 문자열로 변환. (<span style="color:red">업캐스팅 아님.</span>)

```Java
1 + "안녕" //1안녕
1 + "안녕" + 2 //1안녕2
"안녕" + 1 + 2 //안녕12
1 + 2 + "안녕" //3안녕
```

4번째 예제의경우 연산이 좌측부터 시작되기 때문에 1 + 2 기본자료형 연산이 먼저 진행되고 결과값인 3은 뒤에 "안녕"문자열과 연산되어 3이 String으로 변환됨.
