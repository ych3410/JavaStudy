# 접근 제어자(access modifier)

---

### 1. 접근 제어자(access modifier)

접근 제어자는 멤버 또는 클래스에 사용되어, 해당하는 멤버 또는 클래스를 외부에서 접근하지 못하도록 제한하는 역할을 한다. 

접근 제어자가 붙어있지 않는 멤버변수, 메서드, 생성자가 있다면 **접근 제어자가 default이다.**

> 접근 제어자가 사용될 수 있는 곳 - 클래스, 멤버변수, 메서드. 생성자
>
> 1. Private : 같은 클래스 내에서만 접근이 가능하다.
> 2. default : 같은 패키지 내에서만 접근이 가능하다.
> 3. Protected : 같은 패키지 내에서, 그리고 다른 패기지의 자손클래스에서 접근이 가능하다.
> 4. public : 접근 제한이 전혀 없다.

접근 범위를 간단히 부등호의 형태로 나타내보자면 아래의 형태가 된다.

> public > protected > (default) > private

접근제어자가 어디에 붙고 뭐가 붙을까?

> 1. 클래스 : public, (default)
> 2. 메서드&멤버변수 : public, protected, (default), private
> 3. 지역변수 : 없음

위와 같이 접근 제어자가 붙는다.

### 2. 접근 제어자를 이용한 캡슐화

접근 제어자로 캡슐화를 하는 이유는 클래스나 멤버, 주로 멤버에 접근 제어자를 사용하는 이유는 클래스의 내부에 선언된 데이터를 보호하기 위해서이다. 예를 들어 비밀번호, 데이터를 유효한 값으로 유지하는 등의 상황에쓰이는 것이다.

이러한 내용들을 모두 **데이터 감추기(Data Hiding)** 라고 하며, 객체지향개념의 **캡슐화(encapsulation)** 에 해당하는 내용이다.

이 밖에도 외부에서 접근할 필요가 없는 멤버들을 private로 지정함으로서 복잡성을 줄일 수 있는데 이것 역시 캡슐화이다.

> 접근 제어자를 사용하는 이유
>
> 1. 외부로부터 데이터를 보호하기 위해서
> 2. 외부에는 불필요한, 내부적으로만 사용되는, 부분을 감추기 위해서

접근제어자를 잘쓰게 되면 많은 이점이 있는데 그중에서도 만약 접근제어자가 public이라면 오류난 위치를 찾기가 매우 범위가 넓을 것이다. 그러나 protected라면 public보다 오류의 범위가 줄어들며 private는 클래스 하나만 살펴보면 된다.

다음 코드는 접근제어자가 필요한 이유이자 getter와 setter의 예제이다.

```java
public class Time{
  public int hour;
  public int minute;
  public int second;
}
public class TimeTest{
  Time t = new Time();
  t.hour = 25;
}
```

위 코드는 접근제어자가 public이기 때문에 hour시간의 범위는 0~24사이이지만 접근제어자가 public이기 때문에 hour인스턴스에 제값이 들어가지 못한다. 그러나 다음코드를 보자

```java
public class Time{
  private int hour;
  private int minute;
  private int second;
  
  Time(int hour, int minute, int second) {
    setHour(hour);
    setMinute(minute);
    setSecond(second);
  }
  
  public int getHour() { return hour; }
  public void setHour(int hour){
    if(hour < 0 || hour > 23) return;
    this.hour = hour;
  }
  public int getMinute() { return minute; }
  public int setMinute(int minute){
    if(minute < 0 || minute > 59) return;
    this.minute = minute;
  }
  public int getSecond() { return second; }
  public int setSecond(int second){
    if(second < 0 || second > 59) return;
    this.second = second;
  }
}
public class TimeTest{
  public static void main(String args[]){
    Time t = new Time(12, 35, 30);
		System.out.println(t);
    t.hour = 13;                  //오류 : private변수에 직접 접근이 불가능 하다.
    t.setHour(t.getHour + 1);
    System.out.println(t);        //1시간 후로 변경
  }
}
```

위 코드를 보면 코드가 좀 길어졌지만 get으로 시작하는 메서드로 값을 받아와 set으로 시작하는 메서드가 인스턴스에 값을 넣어준다. 위와 같은 코드를 사용하게 되면 아까전 코드와 달리 값을 받아올때 일정조건에 맞춰 인스턴스의 값이 훼손되는것을 막을 수 있다.

이후에 부모클래스로써 상속할 클래스는 멤버변수가 private가 아닌 protect로 하여 자식 클래스에서 접근할 수 있게 해준다.

위와같이 get으로 시작하는 메서드를 **겟터(getter)** 라고 부르고 **"get멤버변수 이름"** 의 형태로 만든다 또한 set으로 시작하고 멤버변수에 값을 저장해주는 메서드를 **셋터(setter)** 라고 부르고 **"set멤버변수 이름"** 의 형태로 만든다. 겟터와 셋터는나중에도 많이 사용하니 잘기억해두도록 하자.

### 3. 생성자의 접근 제어자

생성자에 접근 제어자를 사용함으로써 인스턴스의 생성을 제한할 수 있다. 보통 생성자의 접근제어자는 클래스의 접근재어자와 같지만, 다르게 지정할 수도 있다.

```java
class Signleton{
  private Singleton() {
    ...
  }
}
```

위코드는 생성자에 private를 붙여 만든 생성자인데 private특징 때문에 같은 클래스 밖에서는 생성자를 주가할 수 없다. praivate생성자를 사용하면 부모클래스가 될 수 없다(부모클래스를 부를려면 생성자를 호출하는데 불가능함). 즉 class앞에 final을 붙임으로서 상속이 안됨을 알려주면 좋다.

```java
class Signleton{
  private static Singleton s = new Signleton(); //getInstance에서 인스턴스를 사용하도록 static임
  private Singleton() {
    ...
  }
  //인스턴스를 생성하지 않고도 사용할 수 있도록 static으로 이어야함
  public static Signleton getInstance(){
    return s;
  }
}
```

위 코드는 public을 붙인 생성자로 외부에서 인스턴스를 사용하도록 할 수있으며, public인 동시에 static이어야한다. public메서드를 통해 인스턴스를 접근하므로 사용하는 인스턴스의 개수를 제한할 수 있다.

---



