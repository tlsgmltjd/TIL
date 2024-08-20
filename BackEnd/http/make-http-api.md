# HTTP API 만들기

도서 관리 API를 설계해야한다면

요구사항

- 도서 목록 조회
- 도서 조회
- 도서 등록
- 도서 수정
- 도서 삭제

API URI 설계

- 도서 목록 조회 `/read-book-list`
- 도서 조회 `/read-book-by-id`
- 도서 등록 `/create-book`
- 도서 수정 `/update-book`
- 도서 삭제 `/delete-book`

이렇게 짜여진 URL 설계가 잘 짜여진 URI 설계일까?

URI 설계에 가장 중요한 것은 **리소스 식별**이다.

리소스란?

- 도서를 등록하고 수정하고 조회하는 것이 리소스가 아니다.
- 도서 등록, 도서 조회.. -> 도서가 리소스

옳은 리소스 식별 방법

- 도서를 등록하고 수정하고 조회하는 것을 모두 배제한다.
- **도서라는 리소스만 식별하면 된다 -> 도서 리소스를 URI에 매핑하면 됨**

API URI 설계 (리소스 식별, URI 계층 구조 활용)

- **도서** 목록 조회 `/books`
- **도서** 조회 `/books/{id}`
- **도서** 등록 `/books/{id}`
- **도서** 수정 `/books/{id}`
- **도서** 삭제 `/books/{id}`

문제점

- 조회, 등록, 수정, 삭제를 어떻게 구분하지??

### 리소스와 행위를 분리

가장 중요한 것은 리소스를 식별하는 것이다.

- URI는 리소스만 식별한다
- 리소스와 해당 리소스를 대상으로 하는 행위를 분리한다.
- **리소스 : 도서**
- **행위 : C R U D**
- 리소스는 명사, 행위는 동사가 된다.
- 행위 (메서드) 는 어떻게 구분하지??
  - HTTP 메서드를 사용하면 된다.