Thread란?
===========

스레드란, 프로세스 (공장)내에서 실제로 작업을 수행하는 주체를 의미한다.  
모든 프로세스에는 한 개 이상의 스레드가 존재하여 작업을 수행한다.  
또한 , 두개 이상의 스레드를 가지는 프로세스를 멀티스레드 프로세스라고 한다.

##Process
- "컴퓨터에서 연속적으로 실행되고 있는 컴퓨터 프로그램"  
- 메모리에 올라와 실행되고 있는 프로그램의 인스턴스(독립적인 개체)
- 운영체제로부터 시스템 자원을 할당받는 작업의 단위
- 실행된 프로그램
- 특징 : 프로세스당 최소 한개의 스레드(메인스레드)를 가지고 있다.
- 한 프로세스가 다른 프로세스의 자원에 접근하려면, 프로세스간의 통신(IPC, inter-process communication)을 사용해야 한다.


## Thread
- *프로세스(실행된 프로그램) 내에서 실행되는 여러 흐름의 단위*
- 프로세스의 특정한 수행 경로
- 프로세스가 할당받은 자원을 이용하는 실행의 단위 



- Thread와 Process의 주요한 차이점 : 동일한 프로세스 내의 스레드는 공유 메모리 공간에서 실행되는 반면, 프로세스는 별도의 메모리 공간에서 실행된다는 점.

## Multi Process
- 멀티 프로세싱이란?  하나의 응용 프로그램을 여러 개의 프로세스로 구성하여 각 프로세스가 하나의 작업을 처리하도록 하는 것, 
- 장점 : 여러 개의 자식 프로세스 중 하나에 문제가 발생하면 그 자식 프로세스만 죽는 것 이상으로 다른 영향이 확산 되지 않는다.


## Multi Thread
- 멀티 스레딩이란?  하나의 응용 프로그램을 여러 개의 스레드로 구성하고 각 스레드로 하여금 하나의 작업을 처리 하도록 하는 것이다.
- 윈도우, 리눅스 등 많은 운영 체제들이 멀티 프로세싱을 지원하고 있지만, 멀티 스레딩을 기본으로 하고 있다
- 웹서버는 대표적인 멀티 스레드 응용프로그램이다.



Thread의 생성과 실행
================
Java에서 스레드를 생성하는 방법에는 2가지 방법이 있다.

1)Runnable 인터페이스를 구현하는 방법  

2)Thread 클래스를 상속받는 방법

두 방법 모두 스레드를 통해 작업하고 싶은 내용을 run()메소드에 작성하면 된다.  

```java
class ThreadEx_1 extends Thread {
    public void run(){
        //작업내용
    }
}

ThreadEx_1 ex1 = new ThreadEx_1();
ex1_start();
```

```java
class ThreadEx_2 implements Runnable{
    public void run(){
        //작업내용
    }
}
ThreadEx_2 ex2 = ThreadEx2();
Thread t = new Thread(Ex2);
t.start();
```

### start()와 run()에 대한 차이와 쓰레드가 실행되는 과정
run()을 호출하는 것은 생성된 쓰레드를 실행시키는 것이 아니라 단순히 클래스에 속한 메서드 하나를 호출하는 것이다.   
반면에 start()는 새로운 쓰레드가 작업을 실행하는데 필요한 호출 스택을 생성한 다음에 run()을 호출해서, 생성된 호출스택에 run() 이 첫번째로 저장되게 한다.



### Thread를 잠시 일시 정지 시키는 법
실행중인 스레드를 잠시 멈추게 하고 싶다면 Thread클래스의 정적 메소드인 sleep()메소드를 사용하면 된다  

사용법 : 

```java
try{
    Thread.sleep(1000);
}catch(InterruptedException e){
    e.printStackTrace();
}
```
매개값에는 얼마동안 일시 정지 상태로 있을것인지 밀리세컨단위로 시간을 알려주면 된다.  
1000이라는 값을 주면 스레드는 1초동안 일시정지 된다.  일시정지 상태에서 주어진 시간이 되기 전에 interrupt()메소드가 호출되면,  
InterruptedException이 발생하기 때문에 예외 처리가 필요하다.




```java

@SpringBootApplication
public class PracApplication {

	public static void main(String[] args) {
		Toolkit toolkit =  Toolkit.getDefaultToolkit();
		for(int i=0; i<10; i++){
			toolkit.beep();
			System.out.println("3초 후 Beep음이 울립니다.");
			try {
				Thread.sleep(3000);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	}

}

```