# Iterator

- 컬렉션(리스트, 셋)에 저장된 데이터 하나씩 접근하는데 사용되는 인터페이스
- Enumeration은 Iterator의 구버전
    
    ![Untitled](Iterator%20d9300028f8f14e76a31f0ed52970b787/Untitled.png)
    
- 참고로 ListIterator는 previous()도 있기에 이전버전도 접근가능(양방향), 리스트에만 사용가능(셋 불가)

- 사용법
    
    ```java
    Collection c = new ArrayList();
    Iterator it = c.iterator();
    while(it.hasNext()){
    	System.out.println(it.next());
    }
    ```
    
    map의 경우에는 Collection 인터페이스가 아니기에
    
    ```java
    Map map = new HashMap();
    Iterator it = map.entrySet().iterator(); //entrySet()은 키,벨류 쌍을 세트형식으로 반환
    ```
    
- 주의
    
    ```java
    ArrayList list = new ArrayList();
    list.add("1");
    list.add("2");
    list.add("3");
    
    Iterator it = list.iterator();
    list.add("4"); //이터레이터 만든 후 리스트에 값 변경하면 예외발생
    ```