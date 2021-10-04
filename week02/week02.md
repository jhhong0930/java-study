### 상속

상속: 기존의 클래스를 재사용하여 새로운 클래스를 작성하는 것

- 코드의 중복을 제거하고 재사용성을 높여 생산성과 유지보수에 용이하다

```java
// 상속을 구현하는 방법
class Chiled extends Parent {
    ...
}
```

- 이 두 클래스는 서로 상속 관계에 있다고 하며 상속해주는 클래스를 '조상 클래스', 상속 받는 클래스를 '자손 클래스'라 한다
  - 조상 클래스: 부모(parent) 클래스, 상위(super) 클래스, 기반(base) 클래스
  - 자손 클래스: 자식(child) 클래스, 하위(sub) 클래스, 파생된(derived) 클래스

![image-20210929233258933](https://user-images.githubusercontent.com/76515226/135292195-b0c88eb2-5fb9-4283-adc3-53fc9c8e2ad3.png)

- 자식 클래스는 부모 클래스의 모든 맴버를 물려받으므로 자식 클래스가 부모클래스를 포함하는 관계로 설명할 수 있다

```java
class Tv {
    boolean power;
    int channel;
    
    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { -- channel; }
}

class CaptionTv extends Tv {
    boolean caption;
    void displayCation(String text) {
        if (captino) {
            System.out.println(text);
        }
    }
}

class CaptionTvTest {
    public static void main(String args[]) {
        CaptionTv ctv = new CaptionTv();
        ctv.channel = 10;
        ctv.channelUp();
    }
}
```

![image-20210929235032639](https://user-images.githubusercontent.com/76515226/135293398-727ebcc9-e660-46cb-831d-6af41fcb23b9.png)

### 포함 관계

클래스를 재사용할 때 상속이외에도 포함관계를 맺어 클래스를 재사용할 수 있다

```java
class Circle {
    int x; // 원점의 x좌표
    int y; // 원점의 y좌표
    int r; // 반지름
}

class Point {
    int x;
    int y;
}

// Point 클래스를 재사용하여 Circle 클래스 작성
class Circle {
    Point c = new Point();
    int r;
}
```



### 클래스간의 관계 결정하기

클래스를 작성할 때 상속관계를 맺어 줄 것인지 포함관계를 맺어 줄 것인지는 **~은 ~이다(is-a)**와 **~은 ~을 가지고 있다(has-a)**를 넣어서 문장을 만들어보면 클래스 간의 관계가 보다 명확해 진다

- 원(Cricle)은 점(Point)이다 - Circle is a Point - 상속 관계
- 원(Circle)은 점(Point)을 가지고 있다 - Cricle has a Point - 포함 관계

### 단일 상속

C++ 에서는 여러 조상 클래스로부터 상속받는 것이 가능한 다중상속을 허용하지만 자바는 단일 상속만을 허용한다

다중 상속을 허용하게 된다면 다음과 같은 문제가 있다

- 두 개의 조상 클래스에 선언부만 같고 서로 다른 내용의 두 메서드가 있다면 구별을 하기 힘들다
- 이러한 문제점들을 해결하기 위해 단일 상속만을 허용한다
- 단일 상속이 하나의 조상 클래스만 가질 수 있기 때문에 클래스 간의 관계가 보다 명확해진다

### Object 클래스

- Object 클래스는 모든 클래스의 상속계층도의 최상위에 있는 조상클래스다
- 컴파일러는 자동적으로 다른 클래스로부터 상속을 받지 않는 클래스들은 Obejct 클래스를 상속받도록 만든다

### 오버로딩 & 오버라이딩

- 오버로딩(overloading): 한 클래스 내에 같은 이름의 메서드를 여러 개 정의하는 것(new)

  - 오버로딩이 성립되기 위해서는 메서드의 이름이 같고 매개변수의 개수 혹은 타입이 달라야 한다

  - print구문도 사실 호출 시 매개변수로 지정하는 값의 타입에 따라서 호출되는 print메서드가 달라진다, 오버로딩의 아주 좋은 예

  - 근본적으로 같은 기능을 하는 메서드들이지만 만약 이름이 모두 다르면 기억하기도, 이름을 작성하기도 부담이 된다

  - 이럴때 오버로딩을 통하여 같은 기능을 하는 메서드들을 하나의 이름으로 통일하게 되면 메서드의 이름도 기억하기 쉽고 같은 기능을 하겠구나 라고 예측을 할 수 있다

    ```java
    void println()
    void println(boolean x)
    void println(char x)
    void println(int x)
    void println(long x)
    void println(Object x)
    void println(String x)
    
    // 만약 모든 메서드 이름이 달라야 한다면..
    void println()
    void printlnBoolean(boolean x)
    void printlnChar(char x)
    void printlnDouble(double x)
    void printlnString(String x)
    ```

- 오버라이딩(overriding): 조상 클래스로부터 상속받은 메서드를 재정의해서 사용하는 것(change, modify)

  - 오버라이딩이 성립되기 위해서는 메서드의 이름, 매개변수, 반환타입이 같아야 한다. 즉, 선언부가 일치해야 한다

  - 접근 제어자는 조상 클래스의 메서드보다 좁은 범위로 변경할 수 있고, 조상 클래스보다 많은 수의 예외를 선언할 수 없다

  - 인스턴스 메서드를 static으로, 혹은 그 반대로 변경할 수 없다

    ```java
    public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }
    
    @Override
    public String toString() {
        return "User{" + "username='" + username + '\'' + ", password='" + password + '\'' + '}';
    }
    ```

### 제어자

- 접근 제어자
  - private: 같은 클래스 내에서만 접근이 가능
  - protected: 같은 패키지 내, 다른 패키지의 자손 클래스에서 접근이 가능
  - default: 같은 패키지 내에서만 접근이 가능
  - public: 접근 제한이 없다
- 접근 제어자를 사용하는 이유?
  - 외부로부터 데이터를 보호하기 위하여
  - 외부에는 불필요한, 내부적으로만 사용되는 부분을 감추기 위하여
- static - 클래스의, 공통적인
  - 클래스 변수는 인스턴스 변수와 달리 하나의 변수를 모든 인스턴스를 공유하기 때문에 같은 값을 가진다
  - static 초기화 블럭은 클래스가 메모리에 올라갈 때 단 한번만 수행된다
- final - 마지막의, 변경될 수 없는
  - 클래스에 final이 붙게되면 확장될 수 없는 클래스가 된다
  - 메서드에 final이 붙게되면 오버라이딩을 통해 재정의할 수 없다
  - 변수에 final이 붙게되면 값을 변경할 수 없는 상수가 된다
- abstract - 추상의, 미완성의
  - 메서드의 선언부만 작성하고 실제 수행내용은 구현하지 않은 추상 메서드를 선언하는데 사용
  - 추상 클래스는 동일한 부모를 가지는 클래스를 묶는 개념으로, 상속을 받아서 기능을 확장시키는 것이 목적이다
  - 추상 클래스와 인터페이스?
    - 인터페이스는 추상 클래스보다 한 단계 더 추상화된 클래스
    - 추상 클래스에는 일반 메서드를 구현할 수 있지만, 인터페이스는 모든 메서드가 추상 메서드이다

