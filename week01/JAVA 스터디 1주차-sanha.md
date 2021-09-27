# JAVA 스터디 1주차

- 클래스와 객체, 변수와 메서드, 생성자

----------------------------------------

![](https://images.velog.io/images/9sanha/post/0200d3c1-5558-4dda-a382-e5de0988eb8c/Slide1.jpg)

![](https://images.velog.io/images/9sanha/post/53ec089e-0e21-40a9-9647-bc5d4a1d1463/Slide2.jpg)

![](https://images.velog.io/images/9sanha/post/a76f980d-054f-4273-8bfd-80ed05db4be3/Slide3.jpg)

![](https://images.velog.io/images/9sanha/post/f66ac13c-7cac-4ab7-9de5-a3324dacd29b/Slide4.jpg)

![](https://images.velog.io/images/9sanha/post/5e5bce71-3330-4609-88c7-c93cff51a4be/Slide5.jpg)

![](https://images.velog.io/images/9sanha/post/6b4dde11-c4e3-4d93-ba96-881e629b58a1/Slide6.jpg)

![](https://images.velog.io/images/9sanha/post/427bce04-1015-4a5a-b57b-292d4ff5dd68/Slide7.jpg)

![](https://images.velog.io/images/9sanha/post/9516d8c7-5056-475d-a389-0f1eb281fab9/Slide8.jpg)

![](https://images.velog.io/images/9sanha/post/1d6fae10-0420-467e-818a-01285c6714a7/Slide9.jpg)

![](https://images.velog.io/images/9sanha/post/495382f5-0375-42d3-a25f-9b173691bca6/Slide10.jpg)

![](https://images.velog.io/images/9sanha/post/8457cd1f-fc6a-44d1-820b-554c474641cf/Slide11.jpg)

![](https://images.velog.io/images/9sanha/post/68f7085c-a892-49d1-8184-3dc7e986ebdc/Slide12.jpg)

![](https://images.velog.io/images/9sanha/post/ed233efc-6f70-490d-8c0e-f4d1a4b1e2d1/Slide13.jpg)

![](https://images.velog.io/images/9sanha/post/0b31baec-d47d-4a60-8f1a-e5930d87fdfd/Slide14.jpg)

![](https://images.velog.io/images/9sanha/post/d0bf1656-3a3b-4fe6-b190-a3b0f4d1bccc/Slide15.jpg)

![](https://images.velog.io/images/9sanha/post/bbbc50bc-4c5d-4c7c-8d15-6fc9d43c69ac/Slide16.jpg)

![](https://images.velog.io/images/9sanha/post/418953af-6914-4866-8197-94f24cbabb62/Slide17.jpg)

![](https://images.velog.io/images/9sanha/post/14285175-e639-4c2d-b9d6-3717cdac2fc2/Slide18.jpg)

![](https://images.velog.io/images/9sanha/post/7322898b-05d5-4661-bf76-d80a3e903ca4/Slide19.jpg)

![](https://images.velog.io/images/9sanha/post/1765825d-bc4b-4d74-88d0-b058d3c2cea2/Slide20.jpg)

![](https://images.velog.io/images/9sanha/post/a24b01d8-0dcb-4baf-a480-40c5d108b0c2/Slide21.jpg)

![](https://images.velog.io/images/9sanha/post/9b6e8142-85f3-46a8-a1e2-8e1f3a8b3811/Slide22.jpg)

![](https://images.velog.io/images/9sanha/post/3ad4de9c-6f8f-49aa-9c9b-15263dcad6f7/Slide23.jpg)

![](https://images.velog.io/images/9sanha/post/16a0d8c8-7bec-446b-8329-bececd20c2f7/Slide24.jpg)

## 변수, 생성자

클래스는 보통 멤버 변수, 생성자, 메소드로 구성됩니다.

**멤버변수**는 **클래스 내, 메소드 외에 정의된 변수**입니다! 

저희는 이 멤버변수를 **메소드와 생성자에 사용**할 수도 있고 **클래스 밖(다른 클래스 안)에서 직접 값을 바꿀 수도 있**습니다!

``` java
//class는 대문자로 시작
class Example {
    int memberVar;
    String exampleVar;
}
```

**생성자**는 **객체가 만들어 질 때 자동으로 실행되는 메소드** 입니다! 

**클래스 이름과 같은 이름을 쓰는 메소드**는 전부 생성자입니다!

``` java
class Example {
    int memberVar;
    String exampleVar;
    public example(){} //인자가 없으면 기본 생성자입니다!
    public example(int a, String b){
        this.memberVar = a; // this는 java의 예약어입니다!
        this.exampleVar = b;// 생성자, 메소드에서 사용되는 this는 this를 가동시킨 객체를 가르킵니다!
        System.pit.print("객체 생성시 타입에 맞게 인자를 넣으면 이 생성자가 실행됩니다!");
    }
}
```

## + 메소드

​	저희가 클래스에 정의하는 메소드 말고도 많은 메소드가 있습니다! 

​	저희가 콘솔창에 출력할 때 쓰는 println()도 메소드, size(), equals() 등등 자바에서 제공해주는 메소드입니다!

