## 영속성 컨텍스트란

JPA에서 가장 중요한 용어로 엔티티를 **영구저장하는 환경**이라는 뜻이다.

영속성 컨텍스트엔 엔티티 메니져로 접근하고 이는 매 요청마다 EntityManagerFactory에서 생성된다.

엔티티 메니져는 DB에서 커넥션을 가져와 사용하고 반납한다.

영속성 컨텍스트에서 `flush` 가 일어나면 그때 DB에 쿼리가 나간다.

### 생명주기

엔티티는 앞서말했듯 영속성 컨텍스트에 저장되기 위해 엔티티 메니져로 관리되고 생명주기를 가진다.

- 영속 : 영속성 컨텍스트에 저장됨
- 비영속 : 아직 영속성 컨텍스트에 저장되지 않음
- 준영속 : 영속성 컨텍스트에 저장되었다가 `despatch` (분리)된 상태
- 삭제 : 삭제됨(실제 DB에서 삭제)

### 특징과 장점

영속성 컨텍스트는 엔티티를 식별자(@Id로 매핑한거)로 관리하기에 이는 필수이다.

JPA는 트렌젝션이 커밋되면 영속성 컨텍스트에 있는 모든 변경사항을 DB에 반영하고 이를 `flush` 라고 한다. 데이터베이스와 동기화하는 작업이다. **커밋은 플러시 다음에 실행됨**

**1차캐시**

영속성 컨텍스트 내부에 캐시가 있어 엔티티가 영속이 된다면 이곳에 저장된다. 이후 다시 엔티티를 조회할때 먼저 1차캐시를 체크하고 DB를 확인하기 때문에 효율적이다.

**쓰기지연**

엔티티를 영속화한다고 바로 쿼리가 나가는 것이 아닌 위에서 말했듯 `flush` 가 일어나면 쓰기지연 저장소에 쌓인 쿼리들을 한번에 DB에 보낸다.

**변경감지**

엔티티 수정을 위해 엔티티를 불러오고 데이터를 변경하면 영속성 컨텍스트에서 자동으로 변경감지를 해서 쿼리를 짜고 `flush` 된다.

**동일성 보장**

캐시저장소 덕분에 같은 객체를 두 번 조회하면 그 둘은 다른 인스턴스가 아닌 같은 인스턴스임이 보장된다.