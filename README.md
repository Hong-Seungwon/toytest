# JPA와 Rest API 활용한 게시판
## 참고 자료 : 스프링 부트와 AWS로 혼자 구현하는 웹서비스 및 관련 블로그들

# 목차
- [요구사항 분석](요구사항-분석)
- [개발 환경](개발-환경)
- [구현 기능](구현-기능)

### 요구사항 분석
1. 회원 가입

- 유효성 검사
  - 이메일 형식 패턴
  - 비밀번호 8~16자이며, 영문 대/소문자, 숫자, 특수 문자 사용
  - 닉네임은 2~10자이며, 특수 문자를 제외한 한글(ㄱ-ㅎ가-힣), 영문(a-zA-Z), 숫자(0-9), 언더바(_) 사용
  - 공백 혹은 빈칸이 있는지 확인하고 있다면, 해당 부분 메시지 출력

- 중복 확인
  - 데이터 베이스에 존재하는 아이디, 이메일, 닉네임인 경우 "이미 사용하는 OOO입니다."로 출력
  - 중복 없으면 회원 가입 후 로그인 페이지로 이동

2. 로그인
- 비로그인 이용 가능
  - 회원 가입
  - 로그인
  - 게시글 목록 조회
  - 게시글 상세 보기
  - 게시글 검색
  - 올바르지 못한 경로거나 로그인 필요한 경우 로그인 페이지로 이동

- 로그인 검사
  - 아이디 및 비밀번호 불일치 시 "아이디 또는 비밀번호가 일치하지 않습니다." 출력
  - 이외의 다른 에러 메시지 처리
  - 로그인 성공 시 index 페이지로 이동
  
- 소셜 로그인
  - 구글, 네이버 로그인
  - 데이터베이스에 아이디 존재 시 데이터 정보 유지
  
3.  회원정보 수정
- 회원정보 수정은 비밀번호, 닉네임만 가능
- 빈칸 혹은 공백으로 된 경우 “공백 또는 입력하지 않은 부분이 있습니다.” 메시지 출력
- 닉네임이 중복 확인을 통해 중복일 경우 “이미 사용중인 닉네임입니다.” 메시지 출력
- 닉네임은 최소 2~10자이며, 특수문자를 제외한 한글 (ㄱ-ㅎ가-힣), 알파벳 대소문자(a-zA-Z), 숫자(0-9)만 가능
- 비밀번호 수정 또한 최소 8자~16자이며, 영문 대/소문자, 숫자, 특수문자를 사용
- 수정 완료 시 수정 날짜 업데이트 하기

4. 게시판
- 게시글
  - 작성 및 수정 시 제목과 내용 빈칸 혹은 공백으로 작성하지 않기
  - 내가 작성한 게시글만 수정 및 삭제 가능
  - 비로그인으로 게시글 작성 시 로그인 페이지로 이동
  
- 댓글
  - 로그인한 사용자만 가능
  - 작성 및 수정 시 제목과 내용 빈칸 혹은 공백으로 작성하지 않기
  - 수정 및 삭제는 작성한 아이디만 가능
  - 게시글 삭제 시 댓글 데이터도 같이 삭제

### 개발 환경
- *IntelliJ*
- *SpringBoot 2.7.6* 
- *JAVA 11 ver.*
- *Maven 3.6.3*
- *Tomcat 9.0*
- *MySQL*
- *Mustache*
- *Javascript*
- *jQuery*
- *Ajax*
- *HTML5&CSS3*
- *JPA(Spring Data JPA)*
- *Spring Security 5.6.2*
- *OAuth 2.0*
- *Validation*

### 구현 기능
1. 게시판 - CRUD 기능, 조회수, 페이징 및 검색 처리
2. 사용자 - Security 회원가입 및 로그인, OAuth 2.0(구글, 네이버 로그인), 회원정보 수정, 회원가입 시 유효성 검사 및 중복 검사
3. 댓글 - CRUD 기능
