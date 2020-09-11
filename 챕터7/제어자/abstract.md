# abstract - 추상의, 미완성의

---

### 1. abstract란?

abstract는 **'미완성의'** 의미를 가지고 있다. 메서드의 선언부만 작성라고 실제 수행내용은 구현하지 않은 추상 메서드를 선언하는데 사용된다. 

클래스에 사용되어 클래스 내에 추상메서드가 존재한다는 것을 쉽게 알 수 있게 해준다.

> **abstract가 사용되는 곳 : 클래스, 메서드**

추상 클래스는 아직 완성되지 않은 메서드가 존재하는 **'미완성된 설계도'** 이므로 인스턴스를 생성할 수 없다.

~~~java
abstract class AbstractTest{    //추상 클래스(추상 메서드를 포함한 클래스)
  abstract void move();         //추상 메서드(구현부가 없는 메서드)
}
~~~

매우 가끔 추상메서드가 없는 abstract 클래스를 만드는 경우가 있다. 예를 들어 java, awt, event는 아래와 같이 아무런 내용이 없는 메서드들만 정의되어 있다. 그래서 인스턴스를 생성하지 못하도록 클래스 앞에 제어자 **'abstract'** 를 붙여 놓는다.

~~~java
public abstract class WindowAdqpter{
  implements WindowListener, WindowStateListener, WindowFocusListener{
    public void windowOpened(WindowEvent e) {}
    public void windowClosing(WindowEvent e) {}
    public void windowClosed(WindowEvent e) {}
    public void windowIconified(WindowEvent e) {}
    ...
  }
}
~~~

이 경우 사실 클래스가 쓸모가 없지만 다른 클래스가 이 클래스를 상속받아서 일부의 원하는 메서드만 오버라이딩해도 된다는 장점이 있다. 만일 이 클래스가 없다면 아무런 내용도 없는 메서드를 잔뜩 오버라이딩 해야한다. 

사실 인터페이스를 아직 배우지 않았으니 '이런경우도 있구나'라고 참고하길 바란다.

---

