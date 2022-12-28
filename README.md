## JDBC 프로그래밍 실습

### **목표**
1. JDBC 프로그래밍을 실습한다.
2. 실습한 JDCB 코드 리팩토링 및 DB 커넥션 풀을 적용한다.
   - DBCP(Database Connection Pool)
   - 미리 일정량의 DB 커넥션을 생성해서 풀에 저장해 두고 있다가 HTTP 요청에 따라 필요할 때 풀에서 커넥션을 가져다 사용하는 기법
   - 참고로 스프링 부트 2.0 부터는 디폴트 커넥션 풀로 HikariCP 사용


### JDBC 개념 소개 및 DB 커넥션 풀 개념 소개
- JDBC(Java Database Connectivity)
    - 자바 애플리케이션에서 DB 프로그래밍을 할 수 있도록 도와주는 표준 인터페이스 (DBMS의 종류는 상관이없다.)
    - JDBC 인터페이스들을 구현한 구현체들은 각 데이터베이스 벤더 사 들이 제공 = JDBC Driver
- DBCP(Database Connection Pool)
    - 미리 일정량의 DB 커넥션을 생성해서 풀에 저장해 두고 있다가 HTTP 요청에 따라 필요할 때 풀에서 커넥션을 가져다 사용하는 기법
    - 참고로 스프링 부트 2.0 부터는 디폴트 커넥션 풀로 HikariCP 사용
- 💡 **커넥션 풀 사용시 유의 사항**
    - **커넥션의 사용 주체는 WAS 스레드**이므로 커넥션 개수는 **WAS 스레드 수와 함께 고려**해야 함
        - 여기서 말하는 WAS 스레드는 이전 시간에 만들었던 HTTPWebServer에서 만들었던 것
    - **커넥션 수를 크게 설정**하면 메모리 소모가 큰 대신 동시 접속자 수가 많아지더라도 사용자 대기 시간이 상대적으로 줄어들게 되고, 반대로 **커넥션 개수를 작게 설정**하면 메모리 소모는 적은 대신 그만큼 대기시간이 길어질 수 있음. 따라서 **적정량의 커넥션 객체를 생성해 두어야 함**
    - DB 커넥션 풀 적용을 하려면 DataSource를 사용한다.
        - 커넥션 획득하기 위한 표준 인터페이스, HikariCP의 DataSource 사용


### reference
패스트캠퍼스 : 10개 프로젝트로 완성하는 백엔드 웹개발(Java/Spring) 초격차 패키지 Online.
