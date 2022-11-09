## 10개 프로젝트로 완성하는 백엔드 웹개발(Java/Spring) 초격차 패키지 Online.

part1. 나만의 MVC 프레임워크 만들기

**목표**
1. JDBC 프로그래밍을 실습한다.
2. 실습한 JDCB 코드 리팩토링 및 DB 커넥션 풀을 적용한다.
   - DBCP(Database Connection Pool)
   - 미리 일정량의 DB 커넥션을 생성해서 풀에 저장해 두고 있다가 HTTP 요청에 따라 필요할 때 풀에서 커넥션을 가져다 사용하는 기법
   - 참고로 스프링 부트 2.0 부터는 디폴트 커넥션 풀로 HikariCP 사용

