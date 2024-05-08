# JSP 블로그 프로젝트 (https://github.com/codingspecialist/Jsp-Blog-V5)

## 15강
- JSTL 태그 라이브러리
```
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>

<c:if>
</c:if>

<c:choose>
<c:when>
</c:when>
<c:otherwise>
</c:otherwise>
</c:choose>
```

## 8강

사용자 -> 요청 -> 컨트롤러 -> 서비스 - > 레포지토리 - DAO(DB), 네트워크(통신)

사용자가 브라우저로 요청 시 응답은 HTML
사용자가 App으로 요청 시 응답은 Data(JSON)

회원가입

- 메인화면
board/list.jsp


## 7강
1. web.xml
2. context.xml
3. DB.java (static으로 만드는이유)
4. DBTest.java (삭제)
5. MySQL 라이브러리
6. filter
7. charConfig

## 6강



Model과 DTO의 차이

서비스
1. 회원가입

컨트롤러

## 5강(MIME타입 코딩실습)

ApiServerTest.javva
- localhost:8080/blog/test
- POST
- 키 food
- 값 soup, ramen
- Content-Type이 있으면 body로 보내라는 것
- 



## 4강
- http 통신 -> 헤더, 바디
- 클라이언트가 요청 시 서버가 응답
- 서버는 2진데이터로 보내고 클라이언트는 2진 데이터를 역직렬화 해야함
- 역직렬화를 하기위해서는 헤더가 필요함
- 바디에는 직렬화된 데이터
- 결론은 헤더를 보고 바디를 분석이 가능하다.
- MIME 타입 (ex avi의 mime타입 video/x-msvideo)
- 
- Header
- Body
- Serializable
- 헤더를 보고 바디를 분석하여 역직렬화
- MIME
- Content-Type
- 

## 3강

- Stateless (연결 지속X)  <-> stateful(채팅)
- http 프로토콜(약속) -> 목적(자원 공유) -> html 문서 공유
- 웹브라우저는 html의 해석기 (ex 아래아한글은 hwp 해석기)
- request a.html
- response a.html
- 







## 2강
웹서버의 개념

http

Apache

프로세스 : 실행중인 프로그램

JSP : html 안에 자바파일이 있는 파일

jsp파일은 웹브라우저가 이해하지 못함

웹서버는 jsp 파일을 받으면 was서버에게 던짐

was서버는 jsp파일을 서블릿(자바)파일로 변환

index.jsp -> index.jsp.java -> 컴파일 -> index.jsp.class -> 실행 -> index.html






## 환경

- windows10
- jdk1.8
- tomcat9.0
- sts tool(4.9)
- mysql8.0
- postman
- lombok
- gson (json파싱)
- 인코딩 utf-8
- git

## MySQL 데이터베이스 생성 및 사용자 생성

```sql
create user 'bloguser'@'%' identified by 'bitc5600';
GRANT ALL PRIVILEGES ON *.* TO 'bloguser'@'%';
create database blog;
```

## MySQL 테이블 생성

- bloguser 사용자로 접속
- use blog; 데이터 베이스 선택

```sql
CREATE TABLE user(
    id int primary key auto_increment,
    username varchar(100) not null unique,
    password varchar(100) not null,
    email varchar(100) not null,
    address varchar(100),
    userRole varchar(20),
    createDate timestamp
) engine=InnoDB default charset=utf8;

CREATE TABLE board(
    id int primary key auto_increment,
    userId int,
    title varchar(100) not null,
    content longtext,
    readCount int default 0,
    createDate timestamp,
    foreign key (userId) references user (id)
) engine=InnoDB default charset=utf8;

CREATE TABLE reply(
    id int primary key auto_increment,
    userId int,
    boardId int,
    content varchar(300) not null,
    createDate timestamp,
    foreign key (userId) references user (id) on delete set null,
    foreign key (boardId) references board (id) on delete cascade
) engine=InnoDB default charset=utf8;
```


## 1강

localhost:8080 mywork폴더
localhost:8080/blog mywork폴더의 blog폴더의 webcontent 폴더 진입

web.xml 
welcome-page

--------------------------------------------------------------------------

github 올리기

Repostory name : jsp-Blog-V5

git bash

git init

git add .

git commit -m "1. JSP블로그 환경설정 완료(DB생성, 테이블생성, README 생성)

git remote add origin 

git push origin master


