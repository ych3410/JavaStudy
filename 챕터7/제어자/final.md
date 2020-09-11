#  final - 마지막의, 변경될 수 없는

---

### 1.final?

**final**은 **'마지막의', '변경될 수 없는'** 의 의미를 가짐, 거의 모든 대상에 사용 될 수 있다. 

> final이 붙을 수 있고 붙으면?
>
> 1. **(멤버 & 지역)변수** : 변수앞에 final이 붙는 다면 값을 변경할 수 없게 된다.
> 2. **메서드** : 변경될 수 없는 메서드로, 오버라이딩을 통해 재정의 될 수 없다.
> 3. **클래스** : 변경될 수 없는 클래스, 확장될 수 없는 클래스가 된다. 즉 부모클래스가 될 수 없다.

```java
final class FinalTest{                 //조상이 될 수 없는 final클래스
  final int MAX_SIZE = 10;             //값을 변경할 수 없는 멤버변수(상수선언)
  
  final void getMaxSize(){             //오버라이딩할 수 없는 메서드(변경 불가)
    final int LV = MAX_SIZE;           //값을 변경할 수 없는 지역변수(상수선언)
    return MAX_SIZE;
  }
}
```

### 2. 생성자를 이용한 final멤버 변수의 초기화

final이 붙은 변수는 상수이므로 일반적으로 선언과 초기화를 동시에 하지만, 인스턴스면 수의 경우 생성자에서 초기화 되도록 한다.

클래스 내에 매개변수를 갖는 생성자를 선언하여, 인스턴스를 생성할 때 final이 붙은 멤버변수를 초기화하는데 필요한 값을 생성자의 매개변수로부터 제공받는 것이다.

생성자로 초기화 하는 이유는 각 인스턴스마다 다른 final변수를 갖게 하기 위해서이다.

```java
class Card {
  final int NUMBER;
  final String KIND;
  static int width = 100;
  static int height = 250;
  
  Card(String kind, int num){
    KIND = kind;
    NUMBER = num;
  }
  
  Card(){
    this("HEART", 1);
  }
  public String toString(){
    return KIND + " " + NUMBER;
  }
}

class FinalCardTest{
  public static void main(String args[]){
    Card c = new Card("HEART", 10);
    c.NUMBER = 5;                       //에러 final변수에 대입은 불가능함.
    //출력 : HEART, 10, HEART 10
  }
}
```

---

