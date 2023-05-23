# CG
<hr>
<h3>가비지컬렉션 (쓰레기 수집)</h3>

메모리 관리 기법 중의 하나로, 프로그램이 동적으로 할당했던 메모리 영역 중에서 필요없게 된 영역을 해제하는 기능

쓰레기 수집은 동적 할당된 메모리 영역 가운데 더 이상 사용할 수 없게 된 영역을 탐지하여 자동으로 해제하는 기법이다. 
더 이상 사용할 수 없게 된 영역이란, 어떤 변수도 가리키지 않게 된 영역을 의미한다

<h3>장단점</h3>

쓰레기 수집이 지원되는 환경에서는 프로그래머가 동적으로 할당한 메모리 영역의 전체를 완벽하게 관리할 필요가 없어진다. 쓰레기 수집은 다음과 같은 버그를 줄이거나 완전히 막을 수 있다.

유효하지 않은 포인터 접근: 이미 해제된 메모리에 접근하는 버그를 가리킨다. 만약 이 포인터가 해제되고 새로운 값이 할당되었다면, 잘못된 값을 읽어오게 된다.

이중 해제: 이미 해제된 메모리를 또다시 해제하는 버그를 가리킨다. 일부 메모리 할당 알고리즘에서는, 해제된 메모리를 다시 해제하려고 시도하는 것은 오류를 일으킬 수 있다.

메모리 누수: 더이상 필요하지 않은 메모리가 해제되지 않고 남아있는 버그를 가리킨다. 메모리 누수가 반복되면 메모리 고갈로 프로그램이 중단될 수 있다. 
(접근 가능한 메모리가 증가하여 메모리가 고갈되는 문제는 쓰레기 수집으로도 막을 수 없다)

반면, 쓰레기 수집 기법은 다음과 같은 단점을 갖고 있다.

어떤 메모리를 해제할지 결정하는 데 비용이 든다. 객체가 필요없어지는 시점을 프로그래머가 미리 알고 있는 경우에도 쓰레기 수집 알고리즘이 메모리 해제 시점을 추적해야 하므로, 
이 작업은 오버헤드가 된다.

쓰레기 수집이 일어나는 타이밍이나 점유 시간을 미리 예측하기 어렵다. 때문에 프로그램이 예측 불가능하게 일시적으로 정지할 수 있다. 이런 특성은 특히 실시간 시스템에는 적합하지 않다.

할당된 메모리가 해제되는 시점을 알 수 없다. 자원 할당과 변수 초기화를 일치하는 RAII(Resource Acquisition is Initialization) 스타일의 프로그래밍에서는, 
이것은 자원 해제 시점을 알 수 없다는 것을 의미한다.
