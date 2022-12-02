## OSIV란?

open-session-in-view의 약자 open-entitymanager-in-view라고도 불리는 이 기능은 영속성 컨텍스트의 생존범위를 뷰단 까지 유지해주는 기능이다.

JPA는 데이터 커넥션을 트렌젝션이 시작할때 가져오는데 종료하는 시점이 osiv를 끄냐 키냐에따라 달라진다.

### OSIV를 사용하면

커넥션을 뷰까지 유지하기에 api controller단에서의 **지연로딩**이 가능하다는 장점이있다,하지만 커넥션을 api호출이 종료할때까지 가지고 있기 때문에 api호출이 많은 서비스라면 커넥션이 모자라지고 대기시간이 길어지는 단점이 있다.

### OSIV를 사용안하면

커텍션이 service단까지만 살아있기 때문에 지연로딩의 경우 강제로 다 로딩해야한다.

하지만 트렌젝션 종료시 커넥션도 반납하기에 리소스를 낭비하지 않는다.

Reference

[https://ttl-blog.tistory.com/183](https://ttl-blog.tistory.com/183)

[https://velog.io/@daydream/JPA-OSIV와-성능-최적화](https://velog.io/@daydream/JPA-OSIV%EC%99%80-%EC%84%B1%EB%8A%A5-%EC%B5%9C%EC%A0%81%ED%99%94)