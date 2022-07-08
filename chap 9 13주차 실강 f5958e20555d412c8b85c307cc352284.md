# chap 9 : 13주차 실강

6월 10일 1시반 데이터베이스 비대면 수업 (6월 6일 현충일로 인한 보강)

6월 13일 데이터베이스 기말고사

- ACID property
    - 무조건 외우기 : 약어든 내용이든…
    - 일관성과 고립성은 동시에 실행하는 다른 트랜잭션에 의해서 영향을 받으면 안된다.
        - 동시성 제어와 관련된 특성은 일관성과 고립성이다.
    - 지속성
- 동시에 실행되는 트랜잭션에 대해 아래와 같은 문제가 발생할 수 있다.
    - 갱신 분실
    - 연쇄 복귀
    - 불일치 분석
- 동시성 제어는 위의 문제를 방지하기 위해 실행 순서를 제어해보자
    - 잠금 locking
    - 타임스탬프 timestamp
- serializable schedule
    - serial schedule과 똑같진 않지만 결과는 같게끔 하는 스케줄
- 잠금 locking
    - 운영체제에서는 개발자가 직접 lock을 거는 것과 달리, DBMS가 lock을 알아서 걸어준다.
    - 공유잠금 shared lock, s-lock
        - read()만 가능
    - 배타잠금 exculsive lock, x-lock
        - read(), write() 모두 가능
    - 단순 locking만으로 serializable shcedule이 가능한 것은 아님
- 2PL (2 phase locking protocol)
    - 2단계 잠금 규약
    - 확장 단계 - lock(), 축소 단계 - unlock()
    - serializable shcedule을 보장
    - 교착상태 deadlock, 연쇄 복귀 해결 불가
- 잠금 단위
    - default 단위는 블록