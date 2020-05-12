Trie(트라이)
===========

### 개념
문자열을 효율적으로 저장하기 위한 트리 형태의 자료구조이다. 문자열을 한 글자씩 일일히 비교하는 것보다 훨씬 더 빠르게 탐색이 가능하다.   
하지만 각 노드에서 자식들에 대한 포인터들을 배열로 모두 저장하고 있어 저장 공간의 크기가 크다는 단점이 있다.
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Trie_example.svg/500px-Trie_example.svg.png)

### 시간복잡도
제일 긴 문자열의 길이를 L 총 문자열들의 수를 M이라 할 때,   
생성시 시간복잡도 : O(M*L), 모든 문자열 M개를 가장 긴 문자열 L만큼 삽입.   
탐색시 시간복잡도 : O(L), 가장 긴 문자열의 길이 이하만 탐색하기 때문이다.   

### 공간복잡도
트라이에서는 다음 문자를 가리키는 노드가 필요하다.   
최종 메모리는 O(포인터 크기 * 포인터 배열 개수 * 트라이에 존재하는 총 노드의 개수)가 된다.

### 구현
[github](https://github.com/parkdaye/Algorithm-study/blob/master/src/programmers/kakao/blind2020/LyricsSearch.java, "github link")
