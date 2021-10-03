# 상속

자식 클래스가 부모 클래스로부터 상속을 받게 되면 부모 클래스의 필드와 메서드를 물려받게 된다.

단, 접근제어자가 private을 갖는 필드나 메소드는 상속이 불가하고, 패키지가 다를 경우 접근제어자가 default인 경우도 상속이 불가하다.

또한 자식 클래스는 여러 부모 클래스를 상속 받을 수 없다. 즉, 다중 상속은 불가능하다. 그 이유는 다이아몬드 문제가 발생한다.

다이아몬드 문제란 각각의 부모클래스가 동일한 클래스를 상속 받고 같은 메서드를 오버라이딩 하고 있다면 이때 자식클래스는 어떤 부모클래스의 메서드를 사용할지 선택할 수 없기 때문에 생기는 문제다.

## 상속을 사용하는 이유

중복코드를 줄여주고, 유지보수가 편리하며 통일성과 다형성을 구현할 수 있기 때문에 상속을 사용한다.

## 사용법

상속받을 자식 클래스명 뒤에 extends 키워드를 사용하여 부모 클래스명을 붙여주면 된다.

cf) class 자식클래스명 extends 부모클래스명{....}

## 접근방법 : super, super()

```java
class Parent {

    int a;

    Parent() { a = 10; }

    Parent(int n) { a = n; }

}



class Child extends Parent {
      int a;

    Child() {
        this.a = 20;
        super(); // 부모클래스의 생성자
        }

        void display() {

        System.out.println(a);

        System.out.println(this.a);

        System.out.println(super.a); // 부모클래스의 필드에 접근

        }


    }
```

# 오버라이딩

상속 관계에 있는 부모 클래스에 정의되어있는 메서드를 자식 클래스에서 같은 기능을 갖는 메서드로 재정의 하는 방법이다.

부모클래스의 private 메서드를 제외한 모든 메서드를 가져와서 사용할 수 있다.

## 사용 조건

- 오버라이딩은 메서드의 기능부분을 재정의하는 것이다. 따라서 메서드의 선언부는 동일해야 한다. 반환타입은 부모메서드의 반환타입으로 변환할 수 있는 타입이라면 변경이 가능하다.
- 부모메서드의 접근제어자보다 더 좁은 범위로 변경이 불가능하다.
- 부모메서드의 예외 범위보다 더 큰 범위의 예외를 선언할 수 없다.

# 오버로딩

메서드의 이름은 같지만 선언부의 유형과 개수가 다른 메서드를 생성하는 것을 의미한다. 동일한 기능을 사용하지만 타입이나 개수가 다른 매개변수를 사용하는 메서드가 많이 필요할 경우 오버로딩을 사용하면 코딩시간 단축 및 유지보수에 용이하다.

## 사용방법

```java
int add(int a, int b){
    return a+b;
}
int add(int a, long b){
    return a+b;
}
int add(long a, int b){
    return a+b;
}
int add(long a, long b){
    return a+b;
}
int add(int a, int b, float c){
    return a+b+c;
}
// 매개변수 개수와 타입의 위치가 중요하다.
```

## 가변인자를 사용한 오버로딩

```java
//가변인자가 들어간 메서드 생성시 가변인자는 무조건 선언부의 가장 마지막에 들어가야 한다.  .
String sectionMake(String delim, string...args){
      String result = "";
      int cnt = 0;
      for (String str : args){
        cnt += 1;
        if(cnt == args.size()){
              result += str;
        }else{
              result += str + delim;
          }
      }
      return result;
}
sectionMake(",","사자","호랑이","기린");
sectionMake("-","010","1234","5678");
sectionMake("|","Java","Python");

// 이렇게 가변인자를 사용하면 문제가 없지만 여기서
// 가변인자가 포함된 메서드를 오버로딩하면
String sectionMake(String...args){
      String result = "";
      String delim = "-";
      int cnt = 0;
      for (String str : args){
        cnt += 1;
        if(cnt == args.size()){
              result += str;
        }else{
              result += str + delim;
          }
      }
      return result;
}

sectionMake("010","1234","5678");
// 에러가 발생한다. 따라서 가변인자가 포함된 메서드는 오버로딩을
// 하지 않는 것이 좋다.

```

# Spring에서의 상속, 오버라이딩

```java
public class SuperConfig {
  @Bean
  public String parent(){
    return "나는 부모설정";
  }
}

@Configuration
public class ChildConfig extends SuperConfig {

  @Bean
  public String child() {
    return "자식 설정";
  }

  @Override
  public String parent(){
    return "부모설정 재정의";
  }
}

public static void main(String[] args) {
  ApplicationContext applicationContext = SpringApplication.run(SpringBootApplication.class, args);
  String child = applicationContext.getBean("child", String.class);
  String parent = applicationContext.getBean("parent", String.class);
  System.out.println(child);
  System.out.println(parent);
}
// 이렇게 상속을 받아서 빈 등록이 가능하다. 물론 재정의도 가능하다.
// 이때 오버라이딩 불가능한 정보가 스프링에 존재하기때문에 빈어노테이션 메서드에 final을 사용이 불가능하다.
```

## Spring 상속 어노테이션 @Import

```java
@Configuration
@Import({ DogConfig.class, CatConfig.class })
class MammalConfiguration {
}
//import어노테이션을 사용해서 하나의 설정클래스에 여러개의 설정클래스를 상속받게 할 수 있다.

@ExtendWith(SpringExtension.class) // 단위테스트를 위한 어노테이션
@ContextConfiguration(classes = { MammalConfiguration.class })
// 단위테스트를 위해 해당 클래스의 위치를 찾는다.
class ConfigUnitTest {

    @Autowired
    ApplicationContext context;

    @Test
    void givenImportedBeans_whenGettingEach_shallFindOnlyTheImportedBeans() {
        assertThatBeanExists("dog", Dog.class);
        assertThatBeanExists("cat", Cat.class);
// 여기서 확인 할 수 있듯이 포유류설정클래스에 상속되어진 강아지,고양이 설정 빈들이 사용가능하다.


    private void assertThatBeanExists(String beanName, Class<?> beanClass) {
        Assertions.assertTrue(context.containsBean(beanName));
        Assertions.assertNotNull(context.getBean(beanClass));
    }
}

// import어노테이션을 사용하는 이유는 스프링프레임워크에 존재하는 많은 설정들을
// 그룹화 시켜서 효율적으로 관리가 가능하고 유지보수에 용이할 것 같다.

// ComponentScan 어노테이션도 존재하는데 이것은 SpringBootApplication어노테이션에 포함되어
// 있어서 run시에 component가 붙은 클래스들을 찾아 등록한다. 따라서 import처럼 지정을 할 수 없어서
// 지정이 필요하거나 여러 곳에서 재정의 되어지는 설정값이 있을때는 import를 사용하면 좋을 것 같다.
```

참고사이트: https://www.baeldung.com/spring-import-annotation
