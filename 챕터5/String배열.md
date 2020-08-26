# String배열

---

### 1.String배열의 선언과 생성

배열의 타입이 String인 경우에도 int배열의 선언과 생성방법과 같다. 예를 들어

~~~java
String[] name = new String[5];
~~~

이런식이다.

### 2.String배열의 초기화

초기화 역시 일반 배열과 똑같다. 예를 들어

~~~java
String[] name = new String[3];	
name[0] = "Kim";									//초기화시 ""나 ''를 사용하여 초기화 한다.
name[1] = "Park";
name[2] = "Yi";
~~~

초기화 할때 다른점은 그냥 문자열을 써넣어 초기화 하는 것이 아닌 ""와 ''를 사용해 문자열임을 알려주어 초기화 한다. 다른 배열들과 같이 String배열도 선언과 초기화를 동시에 할 수 있다. 물론 방법도 같다. 

~~~java
String[] name = {"Kim", "Park", "Yi"};		//new String[3]생략 가능
~~~

위와 같이 앞서 말했던 int배열과 같다고 할 수 있다.

### 3. char배열과 String클래스

지금까지 문자열을 저장할 때 String타입의 변수를 사용해왔다. 문자열은 사실 문자인 char의 자료를 연이어 이어놓은 char배열과 같다고 할 수 있다. 근데 왜 String 클래스를 사용하는가? 그이유는 String은 char배열에 여러 기능(매서드)를 추가한 하나의 클래스이기 때문에 문자열을 훨씬 유용하게 사용이 가능하다.

char배열과 String의 차이는 무엇일까? String의 단점이자 차이점인 String객체는 문자열을 읽기만 가능하다. 예를 들어

~~~java
String str = "Java";
str = str +"8";
System.out.println(str);				//Java8출력
~~~

위 코드를 보면 내용수정이 된것처럼 보이지만 String은 읽기만 가능하기 때문에 새로운 String을 생성한 것이다.

String클래스은 어떤 기능(매서드)들이 있을까?

> 1. char charAt(int index) : 문자열에서 해당 위치(index)에 있는 문자를 반환함.
>
> ~~~java
> String str = "abcde";
> char ch = str.charAt(3);			//문자열 str의 4(3번 index이므로 4번째임)번째 문자 'd'를 ch에 저장
> ~~~
>
> 2. Int length() : 문자열의 길이를 반환함.
>
> 3. String substring(int from, int to) : 문자열에서 해당 범위(from ~ to)에 있는 반환함. (to는 범위에 포함되지 않음) 
>
> ~~~java
> String str = :"012345";
> String tep = str.substring(1, 4);		//1~3번 index를 출력(4번index는 포함하지 않음)
> ~~~
>
> 4. Boolean equals(Object obj) : 문자열의 내용이 obj와 같은지 확인한다. 같으면 결과는 true, 다르면 false가 됨
>
> ~~~java
> String str = "abc";
> if(str.equals("abc"))			//abc와 같은지 확인 같으면 1 다르면 0
> ~~~
>
> 5. Char[] toCharArray() : 문자열을 문자배열에(char[])로 변환해서 반환함.
>
> ~~~java 
> char[] arr = {'a', 'b', 'c'};
> String str = new String(arr);			//char -> String
> char[] tmp = str.toCharArray();		//String -> char
> ~~~

---

