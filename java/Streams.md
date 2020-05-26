Stream API
=========================

## 스트림이란?
스트림(Stream)은 자바 8에서 추가된 기능으로 함수형 인터페이스인 람다(lambda)를 활용할 수 있는 기술   
배열이나 컬렉션을 반복문을 순회하면서 요소를 하나씩 꺼내 여러가지 코드를(예를 들어 if 조건문 등) 섞어서 작성했다면   
스트림과 람다를 이용하여 코드의 양을 대폭 줄이고 조금 더 간결하게 코드를 작성   
멀티 스레드 환경에 필요한 코드를 작성하지 않고도 데이터를 병렬로 처리   

## 스트림의 구성
1. 스트림을 생성하는 작업(Stream Source)
2. 스트림을 필터링하거나 요소를 알맞게 변환하는 중간 연산(Intermediate Operations)
3. 최종적인 결과를 도출하는 단말 연산(Terminal Operations)

## 스트림 사용법


## 스트림 사용시 주의사항
forEach 메서드는 병렬 스트림을 사용했을 때 순서를 보장할 수 없다
```
List<Integer> list = List.of(3, 1, 2);

// 매 실행마다 출력 결과가 동일하지 않다.
list.parallelStream().forEach(System.out::println);

// 매 실행마다 동일한 출력 결과
list.parallelStream().forEachOrdered(System.out::println);
```
