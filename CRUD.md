# CRUD
> **C**reate(생성), **R**ead(읽기), **U**pdate(갱신), **D**elete(삭제)<br>
컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리 기능을 묶어서 일컫는 말<br> 데이터베이스 응용 프로그램에서 실행되는 네 가지 기본 작업을 나타내는 데 사용되는 약어
>
 - 많은 프로그래밍 프로토콜과 언에는 이름이 다르고 변형된 CRUD가 존재한다.
    - 예 : Insert, **Select**, Update, Delete 를 지원하는 SQL
    - CRUD Framework 사용하는 다양한 언어 : Java(JOOQ, iBAtis), Phyton(Django), PHP(Propel, Doctrine) 및 .NET(NHibernate, LLBLGEN Pro) 
- 데이터베이스의 구조적 쿼리 언어(SQL)에서 사용되는 데이터베이스 기능을 설명하기 위해 1980년대에 만들어졌다.
---
### VS REST? , 서로 유사한 점이 있다.
**REST 명령**
- POST – 데이터베이스에 새 레코드를 생성
- GET – 데이터베이스에서 가져온 정보를 읽음
- PUT/PATCH – 개체 업데이트
- DELETE - 데이터베이스에서 레코드를 제거

**CRUD 명령**
- CREATE – INSERT 문을 통해 새 레코드를 생성, REST에서 이것은
- READ/RETRIEVE - 입력 매개변수를 기반으로 데이터를 읽음. 
- UPDATE  – 데이터를 덮어쓰지 않고 업데이트합니다.
- DELETE- 데이터베이스에서 데이터를 제거합니다.

**차이**
- REST는 HTTP 명령을 사용하는 리소스 및 Hypermedia를 중심으로 한 아키텍처 시스템, CRUD는 데이터베이스 설정에서 레코드를 유지하기 위한 주기
- CRUD 기능은 REST API에 존재할 수 있지만 REST API는 CRUD 기능으로 제한되지 않음
- REST는 일반적으로 HTTP 명령을 통해 데이터를 사용
- REST와 CRUD의 기능은 유사하지만(위에서 설명한 대로) 동일하지 않음
---
##### References
- [Wikipidia : CRUD](https://ko.wikipedia.org/wiki/CRUD)
- [CRUD vs REST](https://www.logicmonitor.com/blog/rest-vs-crud)
- [CRUD vs REST 무슨 의미인가?](https://leejincha.tistory.com/101)