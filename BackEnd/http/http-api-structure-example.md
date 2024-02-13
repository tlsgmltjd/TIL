# HTTP API 설계 예시

## 도서 관리 시스템

### POST 기반 등록

- 도서 목록 조회 /books GET
- 도서 조회 /books/{id} GET
- 도서 등록 /books/{id} POST
- 도서 수정 /books/{id} PATCH, PUT, POST
- 도서 삭제 /books/{id} DELETE

신규 자원 등록 특징

- 클라이언트는 등록될 리소스의 URI를 모른다
  - 도서 등록 /books -> POST
  - POST /books
- 서버가 새로 등록될 리소스 URI를 생성해준다.
  - HTTP/1.1 201 Created
    Location: /books/123
- **컬렉션 (Collection)**
  - 서버가 관리하는 리소스 디렉터리
  - 서버가 리소스의 URI를 생성하고 관리한다
  - 여기서 컬렉션은 /books

### PUT 기반 등록

- 파일 목록 /files GET
- 파일 조회 /files/{filename} GET
- **파일 등록 /files/{filename} PUT**
- 파일 삭제 /files/{filename} DELETE
- 파일 대량 등록 /files POST

신규 자원 등록 특징

- 클라이언트가 리소스 URI를 알고 있어야한다.
  - 파일 등록 /files/{filename} PUT
  - PUT /files/pororo.png
- 클라이언트가 직접 리소스 URI를 관리한다.
- **스토어 (Store)**
  - 클라이언트가 관리하는 리소스 저장소
  - 클라이언트가 리소스 URI를 알고 관리
  - 여기서 스토어는 /files

> 대부분 Collection 을 사용한다.

## HTML FORM 사용

- HTML FORM은 GET, POST만 지원한다
- AJAX 같은 기술을 사용해서 해결 가능함
- 순수 HTML FORM 만 사용한다고 가정하면 GET, POST만 지원하므로 제약이있다.

* 회원 목록 /members GET
* 회원 등록 폼 /members/new GET
* 회원 등록 /members/new POST
* 회원 조회 /members/new GET
* 회원 수정 폼 /members/{id}/edit GET
* 회원 수정 /members/{id}/edit POST
* 회원 삭제 /members/{id}/delete POST
  > 컨트롤 URI

- HTML Form은 GET, POST만 지원한다
- 컨트롤 URI
  - 이런 제약을 해결하기 위해 동사로 된 리소스 경로를 사용한다
  - POST의 /new /edit /delete가 컨트롤 URI
  - HTTP 메서드로 해결하기 애매한 경우에 컨트롤 URI를 사용한다.
    > **최대한 리소스를 가지고 설계**를 해야하며 애매할 시 대체제로 사용해야한다.

---

###좋은 URI 설계 계념

- 문서 document
  - 단일 개념 (파일 하나, 객체 인스턴스, 데이터베이스 row)
  - ex books/100, /files/edi.png
- 컬렉션
  - 서버가 관리하는 리소스 디렉터리
  - 서버가 리소스의 URI를 생성하고 관리
  - /books
- 스토어
  - 클라이언트가 관리하는 자원 저장소
  - 클라이언트가 리소스의 URI를 알고 관리한다
  - /files
- 컨트롤러, 컨트롤 URI
  - 문서, 컬렉션, 스토어로 해결하기 어려운 추가 프로세스 실행
  - 동사를 리소스 경로에 직접 사용한다
  - /books/{id}/likes
