Java Virtual Machine (JVM)
===============================
JVM 역할은 자바 애플리케이션을 클래스 로더를 통해 읽어 들여 자바 API와 함께 실행하는 것이다.   
그리고 JVM은 JAVA와 OS사이에서 중개자 역할을 수행하여 운영체제에 독립적인 플랫폼을 갖게 해준다.   
자바는 OS 의 메모리 영역에 직접적으로 접근하지 않고 JVM 이라는 가상머신을 이용해서 간접적으로 접근한다.   

또한 JVM은 프로그램의 메모리를 자동으로 관리한다.    
프로그램 실행시 OS에 요청한 사이즈 만큼의 메모리를 할당 받아서 실행하게 된다. 
할당받은 이상의 메모리를 사용하게 되면 에러가 나며 자동으로 프로그램이 종료된다. 
그러므로 현재 프로세스에서 메모리 누수가 발생하더라도 현재 실행중인 것만 죽고, 다른 것에는 영향을 주지 않는다. 
이렇게 자바는 가상머신을 사용함으로써 OS 레벨에서의 memory leak 은 불가능하게 된다는 장점이 있다.   

![image](https://img1.daumcdn.net/thumb/R720x0.q80/?scode=mtistory2&fname=http%3A%2F%2Fcfile23.uf.tistory.com%2Fimage%2F25616D45576B854C3FEAFB)

## JVM 실행과정
1. 프로그램이 실행되면 JVM은 OS로부터 이 프로그램이 필요로 하는 메모리를 할당 받는다. JVM은 이 메모리를 용도에 따라 여러 영역으로 나누어 관리한다.
2. 자바 컴파일러(javac)가 자바소스(.java)코드를 읽어 들여 자바 바이트코드(.class)로 변환시킨다.
3. 이 변경된 Class 파일들을 Class Loader를 통해 JVM 메모리영역(Runtime Data Areas) 영역으로 로딩한다.
4. 로딩된 class파일들은 Execution engine을 통해 해석된다.
5. 해석된 바이트코드는 Runtime Data Areas에 배치되어 실질적인 수행이 이루어지게된다.
이러한 실행과정속에서 JVM은 필요에 따라 Thread Synchronization과 GC같은 관리 작업을 수행한다.

Garbage Collector (GC)
=======================

 Heap 영역의 메모리를 JVM이 판단해 더이상 사용되지 않는 인스턴스는 자동으로 할당 된 메모리를 삭제하는 역할을 담당한다.
 
 ## Reachability
GC는 객체가 가비지인지 판별하기 위해서 reachability라는 개념을 사용한다.   
어떤 객체에 유효한 참조가 있으면 'reachable'로, 없으면 'unreachable'로 구별하고 unreachable 객체를 가비지로 간주해 GC를 수행한다. 
한 객체는 여러 다른 객체를 참조하고, 참조된 다른 객체들도 마찬가지로 또 다른 객체들을 참조할 수 있으므로 객체들은 참조 사슬을 이룬다. 
이런 상황에서 유효한 참조 여부를 파악하려면 항상 유효한 최초의 참조가 있어야 하는데 이를 객체 참조의 root set이라고 한다. 
root set으로부터 시작한 참조 사슬에 속한 객체들은 reachable 객체이고, 이 참조 사슬과 무관한 객체들이 unreachable 객체로 GC 대상이다.   
![image](https://d2.naver.com/content/images/2015/06/helloworld-329631-2.png)
