### 프로그램 오류

1. 컴파일 에러: 컴파일 시에 발생하는 에러
2. 런타임 에러: 실행 시에 발생하는 에러
3. 논리적 에러: 실행은 되지만 의도와는 다르게 동작하는 것

- 에러: 프로그램 코드에 의해서 수습될 수 없는 심각한 오류(메모리 부족, 스택오버플로우 등)
- 예외: 프로그램 코드에 의해서 수습될 수 있는 다소 미약한 오류

### 예외 클래스의 계층구조

![image](https://user-images.githubusercontent.com/76515226/138577316-02b399a2-e3f1-46fa-abfd-6725f9ec1f6c.png)

- Exception 클래스들: 사용자의 실수와 같은 외적인 요인에 의해 발생하는 예외
- RuntimeException 클래스들: 프로그래머의 실수로 발생하는 예외

```java
// 예외 처리를 하려면? try-catch
try {
    // 예외가 발생할법한 문장들
} catch (Exception1 e1) {
    // Exception1이 발생했을 경우 처리를 위한 문장
} catch (Exception2 e2) {
    // Exception2가 발생했을 경우 처리를 위한 문장
    printStackTrace(); // 에외 발생 당시의 호출스택에 있었던 메서드의 정보와 예외 메시지 출력
    getMessage(); // 발생한 예외클래스의 인스턴스에 저장된 메시지를 얻는다
} finally {
    // 예외의 발생여부와 관계없이 항상 수행되어야 하는 문장
}

// 혹은 예외 던지기 throw
User user = repository.findById(id).orElseThrow(
    () -> new NullPointerExection("예외처리 문구")
);
```

- try-catch 문에서 예외가 발생하게 되면 발생한 예외와 일치하는 catch 블럭을 확인 후 해당 문장을 실행
- 에외가 발생하지 않다면 catch 블럭을 거치지 않고 try-catch 문을 빠져나간다
- try -> catch -> finally 순으로 실행되며 예외가 발생하지 않으면 try -> finally 순으로 실행된다

### 지네릭스

- 컴파일 시의 타입체크를 해주는 기능
- 타입의 안정성 제공 및 형변환 생략 가능

```java
class Box {
    Obejct item;
    void setItem(Object item) {this.item = item;}
    Object getItem() {return item;}
}

// 지네릭 타입 T 선언
class Box<T> {
    T item;
    void setItem(T item) {...;}
    T getItem() {,,,;}
}

Box<String> b = new Box<String>();
// Box<String> b = new Box<>(); JDK 1.7부터 생략 가능
b.setItem(new Object()); // 에러, String 이외의 타입 지정불가
b.setItem("ABC");
String item = /*(String)*/ b.getItem(); // 형변환이 필요없다
```

- 모든 객체에 대해 동일하게 동작해야하는 static 맴버에는 사용할 수 없다(static 맴버는 인스턴스변수 참조 불가)
- 지네릭 타입에 extends를 사용하여 특정 타입의 자손들만 대입하게 제한할 수 있다

와일드 카드

- <? extends T> 와일드 카드의 상한 제한, T와 그 자손들만 가능
- <? super T> 와일드 카드의 하한 제한, T와 그 조상들만 가능

### Enum

```java
// 열거형의 정의 및 사용
enum Direction { EAST, SOUTH, WEST, NORTH }

// 추가 정보
@Enumerated(value = EnumType.STRING)
// 이넘타입을 String으로 하는 이유
// 숫자로 되어있으면 필드 추가시 번호가 밀리면서 타입들이 덮어씌워질 수 있다
// String으로 하게되면 이러한 현상을 방지할 수 있다
private UserRoleEnum role;
```

