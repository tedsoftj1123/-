기존의 DB는 하나의 DB와 어플리케이션으로 구성되어있다.

위 경우 서버가 터지거나 부하가 되면 문제가 발생할 수 있다.

이런한 문제를 해결하기 위해 DB를 복제하여 메인으로 master라는 DB를 사용하고 복제본은 slaveDB를 두어 사용하는 replication이라는 기술이 나오게 되었다.

### Replication

---

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aaf1813f-d491-443d-85fe-b78f9d9308c6/Untitled.png)

Replication을 사용하여 master를 복제한 읽기전용 DBslave를 생성한다. 따라서 어플리케이션 실행중 INSERT, UPDATE, DELETE쿼리들은 master가 받아서 처리후 slave에 replication(복제)을 진행하고 slave는 SELECT쿼리만을 처리한다.

어플리케이션 실행중 발생하는 대부분의 쿼리는 select문이다. replication을 사용할 시 메인으로 사용되는 masterDB에는 부하를 줄여주고 slaveDB를 늘려줌으로써 성능향상효과를 얻을 수 있다.