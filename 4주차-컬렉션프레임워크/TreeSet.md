# TreeSet

이진탐색트리로 구현. 범위탐색과 정렬에 유리.

링크드리스트의 변형임

```java
class Node{
		Node next;
		Object obj;
}
```

```java
class TreeNode{
		TreeNode left;
		Object element;
		TreeNode right;
}
```

![Untitled](TreeSet%20e495a45bd6e9455b946219999bb01fa7/Untitled.png)

ex)TreeSet에 7,4,9,1,5 저장하면 다음 과정을 거침

![Untitled](TreeSet%20e495a45bd6e9455b946219999bb01fa7/Untitled%201.png)

1. 7: 7저장
2. 4: 7과 비교→ 작으니까 왼쪽에 저장
3. 9: 7과 비교→ 크니까 오른쪽에 저장
4. 1: 7과 비교→ 작으니까 왼쪽으로 이동→ 4와 비교→ 작으니까 왼쪽에 저장
5. 5: 7과 비교→ 작으니까 왼쪽으로 이동→ 4와 비교→ 크니까 오른쪽에 저장

여기서 **단점**: 저장할수록 비교횟수가 증가함. 데이터가 늘어날 수록 저장하는데 시간이 오래 걸림

- **장점**:
1. 범위검색에 유리
    
    ![Untitled](TreeSet%20e495a45bd6e9455b946219999bb01fa7/Untitled%202.png)
    
2. 정렬 유리- 중위순회하면 오름차순으로 정렬된다
    
    ![Untitled](TreeSet%20e495a45bd6e9455b946219999bb01fa7/Untitled%203.png)