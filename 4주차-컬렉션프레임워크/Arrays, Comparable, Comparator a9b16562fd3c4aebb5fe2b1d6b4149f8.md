# Arrays, Comparable, Comparator

# Arrays

Arrays, Objects, Collections 처럼 뒤에 s로 끝나는애들은 배열다루기 편리한 스태틱 메서드 제공함

- 1차원 배열출력, 비교: toString(), equals()
- 다차원 배열 비교, 출력: deepToString(), deepEquals()
- 배열 복사 :copyOf(), copyOfRange()
- 배열 채우기: fill(), setAll()
- 배열 리스트로 변혼: asList()
    
    ```java
    List list = Arrays.asList(new Integer[]{1,2,3,4,5});
    List list = Arrays.asLsit(1,2,3,4,5) //위랑 같음
    ```
    
    - 주의: asList로 반환되는 List는 읽기전용임. 새로 list.add()하면 예외발생
    - 변경가능한 List로 변환하고자 한다면
    
    ```java
    List list = new ArrayList(Arrays.list(1,2,3,4,5)); 이렇게 해야함
    ```
    
- 배열 정렬과 검색: sort(), binarySearch()
    - binarySearch()는 반드시 정렬된 배열에서 사용해야 잘못된결과가 나오지 않음
    
    ```java
    int[] arr = {3,2,1,0,4};
    
    Arrays.sort(arr); //[0,1,2,3,4]
    int idx = Arrays.binarySearch(arr,2); //idx = 2 올바른 결과
    ```
    

# Comparator과 Comparable

숫자, 문자는 정렬 기준이 있음. 오름차순 내림차순. 근데 객체는 기준이 없음.

즉, 객체를 정렬하는데 필요한 메서드를 정의한 인터페이스이다.(정렬기준을 제공)

- Comparable: 기본정렬기준을 구현하는데 사용
- Comparator: 기본 정렬기준 외에 다른 기준으로 정렬하고자할 때 사용

Integer, String, Date들 모두 사실 이미 Comparable을 구현하고 있었음.

![Untitled](Arrays,%20Comparable,%20Comparator%20a9b16562fd3c4aebb5fe2b1d6b4149f8/Untitled.png)

인터페이스 선언부를 보자면, 

위 Integer클래스에서 Comparable의 compareTo()메서드를 구현하고 있는 것을 알 수 있음

![Untitled](Arrays,%20Comparable,%20Comparator%20a9b16562fd3c4aebb5fe2b1d6b4149f8/Untitled%201.png)

예시:

방법1: 점수를 기준으로 하고자할때: Comparable를 상속시킴

```java
class Student implements Comparable{
	int score;
	String name;

	Studnet(int score, String name){
		this.score = score;
		this.name = name;
	}

	public int compareTo(Object obj){
		Student s2 = (Student)obj;

		return this.score - s2.score; //점수기준 낮은순
	}
}
```

방법2: 학생이름을 기준으로 하고자 할떄: Comparator를 구현하는 클래스 하나 새로 만듦.

```java
class NameAscending implements Comparator{
	public int compare(Object o1, Object o2){
		Student s1 = (Student)o1;
		Student s2 = (Student)o2;
		
		return s1.name.compareTo(s2.name);//여기있는 compareTo는 String클래스에 있는거임(사전순 정렬)

	}
	
}
```

```java
public static void main(String[] args){
	Student[] sArr = {
		new Student(100, "abc"),
		new Student(90, "kim",
		new Student(79, "lee"),
		new Student(88, "choi"),
	};
	Arrays.sort(sArr); //점수기준으로 할때
	Arrays.sort(sArr, new NameAscending()): //학생이름으로 기준할때
	
}
```