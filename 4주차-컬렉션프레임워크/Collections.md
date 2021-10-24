# Collections 프레임워크

![Untitled](Collections%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A6%E1%84%8B%E1%85%B5%E1%86%B7%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%20c41f44d6e3b045f5a817945d082dad89/Untitled.png)

Vector, Stack,HashTable,Properties같은 클래스들은 컬렉션프레임워크 이전부터 있던 거라 명명법이 다르다. (List면 ~List로 끝나고 그래야 함.) 가능하면 사용하지 않는게 좋다. 대신 ArrayList, HashMap을 사용하자.

- 인터페이스의 메서드
    
    ![Untitled](Collections%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A6%E1%84%8B%E1%85%B5%E1%86%B7%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%20c41f44d6e3b045f5a817945d082dad89/Untitled%201.png)
    

# List인터페이스

- 중복허용, 저장순서 유지
- 메서드들- 순서를 활용한 기능들 추가됨
    - ex)void add(int index, Obejct element)
        - 기존 컬렉션인터페이스의 add는 더할수만 있고 저장할 위치는 못 정했음.
    
    ![Untitled](Collections%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A6%E1%84%8B%E1%85%B5%E1%86%B7%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%20c41f44d6e3b045f5a817945d082dad89/Untitled%202.png)
    

# Set인터페이스

- 중복허용하지 않고, 저장순서 유지안됨.
- 기존 컬렉션 메소드(동일) + 집합 관련 메서드가 추가 됨.
    
    ![Untitled](Collections%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A6%E1%84%8B%E1%85%B5%E1%86%B7%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%20c41f44d6e3b045f5a817945d082dad89/Untitled%203.png)
    

# Map인터페이스

- 키는 중복될 수 있지만, 값은 중복 허용안함
- 추가메서드에 add가 아닌 put메서드를 사용함
    
    ![Untitled](Collections%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A6%E1%84%8B%E1%85%B5%E1%86%B7%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%20c41f44d6e3b045f5a817945d082dad89/Untitled%204.png)
    
- Hashing이란? 해시함수로 해시테이블에 데이터를 검색, 저장
- HashMap
    - 배열과 링크드 리스트가 조합된 상태
- TreeMap
    - 트리셋과 비슷하지만, 키와 값의 쌍으로 데이터를 저장한다
    - 다수의 데이터에서 개별적인 검색은 TreeMap보다 HashMap이 빠르다
    

![Untitled](Collections%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A6%E1%84%8B%E1%85%B5%E1%86%B7%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3%20c41f44d6e3b045f5a817945d082dad89/Untitled%205.png)

[ArrayList→LinkedList 추가삭제기능 향상 설명](https://www.notion.so/ArrayList-LinkedList-cd78960605774bc78034182819e7a68c) 

[ArrayList→HashMap 검색기능 향상 설명](https://www.notion.so/HashMap-8ad30786c03e4f3d83995d9c695dc697)

[LinkedList→Treemap 범위검색,정렬기능 향상 설명](https://www.notion.so/TreeSet-44d43fa3351841edac3e08b111a42058)