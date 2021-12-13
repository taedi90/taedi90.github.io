---
title: "팀 프로젝트(쇼핑몰 제작) 회고 - 3.코딩 컨벤션"
date: 2021-12-05T00:00:00+09:00
lastmod: 2021-12-13T20:28:00+09:00
hero: 
url: /yi-teamproject-log-3/
description: 
tags: [log]
menu:
  sidebar:
    name: 팀 프로젝트 후기 3
    identifier: Logs-팀 프로젝트 후기 3
    parent: Logs
    weight: 10
---


프로젝트 내내 덕을 많이 본 코딩 컨벤션이다. 하단 링크를 참고하여 간결하게 우리 프로젝트 만의 컨벤션을 정의했는데 기회가 된다면 이것보다도 더욱 정교하게 만들어 보고 싶다.

## 1. Basic

[캠퍼스 핵데이 Java 코딩 컨벤션](https://naver.github.io/hackday-conventions-java/) 을 **`준수`** 하며, JS 의 경우 [Naver JavaScript Style Guide](https://github.com/naver/eslint-config-naver/blob/master/STYLE_GUIDE.md) 를 가급적 `지향`하며 코딩할 것

### 1-1. IDE 설정

`캠퍼스 핵데이 가이드`에 따라 코딩할 수 있도록 IDE Formatter 적용이 가능함

#### 1-1-1. Eclipse

[naver-eclipse-formatter.xml](images/pic-0001.xml)

- 아래 링크 D.1.* 내용 참고
[https://naver.github.io/hackday-conventions-java/#_eclipse](https://naver.github.io/hackday-conventions-java/#_eclipse)

#### 1-1-2. Intellij

[naver-intellij-formatter.xml](images/pic-0002.xml)

- 아래 링크 D.2.* 내용 참고
[https://naver.github.io/hackday-conventions-java/#_eclipse](https://naver.github.io/hackday-conventions-java/#_intellij)

## 2. Variable & Method

변수와 메서드 네이밍 규칙

### 2-1. Common

변수 및 메서드 공통 사항

#### 2-1-1. Naming

- 가급적 이해할 수 있는 쉬운 단어 (***축약X***)
→ mod_date (❌), modify_date (👌🏻)
- camelCase 사용
→ JAVA, Java Script
- snake_case 사용
→ SQL, HTML Attribute
- kebob-case 사용
→ CSS

> DB 테이블 속성 : parent_no  
>   
>   
> DTO 속성 : parentNo  
>   
> JS var : parentNo  
>   
> JS function : checkParentId  
>   
> HTML element id : parent_no  
>   
> CSS : #parent_no { font-size : var(—font-base); }  
>   

~~element id 와 js function 명이 일치하면 onclick 이벤트에서 오류남~~

~~CSS 는 대소문자를 구분하지 않는다?~~

### 2-2. Variable

변수 및 상수 관련

#### 2-2-1. boolean

- ~~가급적 int 자료형 보다 boolean 자료형 사용~~ 
→ sql result 가 int 형으로 반환 됨.
- boolean 자료형의 경우 'is~' 활용
→ isCorrect, isNull

#### 2-2-2. Const

- 상수는 대문자 및 언더바 사용 (JAVA, JS)
→ TEST_COUNT

### 2-3. Method

메서드 관련

#### 2-3-1. check

- true or false 를 판별하는 메서드는 'check~' 표기
→ checkId(user)

#### 2-3-2. getter & setter

- getName(args), setName(args)

#### 2-3-3. DAO & SQL mapper

- insert
→ insertBoard(board)
- update
→ updateBoard(board)
- select
→ boardDto selectBoard(board), List<board> selectBoardList(Board board)
- delete
→ deleteBoard(board)

## 3. Structure

프로젝트 구조

### 3-1. Folder & Package & File

#### 3-1-1. Outline

- 아래 표를 기준으로 프로젝트 구조를 지정

종류|경로|이름 예시|비고
---|---|---|---
Controller|~base_package/controller/|BoardController.java|응답처리, view 업데이트
Service|~base_package/service/BoardService.java	
ServiceImpl|~base_package/service/Impl|BoardServiceImpl.java|비즈니스 로직 처리
Mapper|~base_package/mapper/|BoardMapper.java|데이터 엑세스
 Dto|~base_package/dto/|Board.java|데이터 교환 객체
Config|~base_package/dto/|WebConfig.java|JAVA 기반 설정파일 
Common|~base_package/common/|randomUtil.java|클래스 간 공유 모듈
sqlmap|/resources/sqlmap/|board_SQL.xml|SQL query
css/js/img|/webapp/resources/[css js img]/|sub-item.css|src="js/item.js"
plugins|/webapp/resources/plugins/|-|텍스트 에디터 등
view|/webapp/WEB-INF/views/서비스/|/board/create.jsp	
others|-||kebob-case


- 이후 프로젝트 규모에 따라 controller, service, dao 패키지에 `업무영역`으로 하위 패키지 리팩토링

#### 3-1-2. Naming

- camelCase
→ java class
- snake_case
→ java package
- kebob-case
→ xml, js, css 등 기타 모든 파일명

### 3-2. JAVA Class

본연의 업무에 충실하고 유지보수에 용이하도록 구성

#### 3-2-1. Controller

- 로직 구현 지양
- Service 호출 및 Exception 처리 전담

#### 3-2-2. Service

- 도메인 서비스 지양 → 기능별 세분화 서비스 지향
UserService → UserRegisterService, UserEmailService ...

#### 3-2-3. Dao

- interface 구현 없이 @Mapper 활용

## 4. Coding

코딩 스타일에 관련 된 규정

### 4-1. DTO 활용

프로젝트에서 Dto를 적극적으로 활용하여 유지보수 및 확장이 용이한 환경을 구성한다.

#### 4-1-1. 가급적 DTO 를 사용하여 데이터 처리하기

- Dto attribute
private String id → private UserDto userDto
- Service args
userDto selectUser(int no) → userDto selectUser(userDto)

#### 4-1-2. 객체 분리 사용

- request, response 객체 분리 사용
불필요한 정보 제거

### 4-2. 예외처리

- 예외는 무시하지 말고 처리할 것

### 4-3. 주석처리

- 각 단위별 기능 명시
- 모호한 부분 설명

### 4-4. 클래스 및 메서드 작게 나누기

세부 기능별 분리(모듈화)

- 재사용성 향상
- 가독성 향상
- 유지보수 향상

### 4-5. Unit Test

- Junit 4 사용
- 반드시 TDD를 고수할 필요는 없음
- FIRST 규칙 지향
Fast: 테스트는 빠르게 동작하여 자주 돌릴 수 있어야 한다.
Independent: 각각의 테스트는 독립적이며 서로 의존해서는 안된다.
Repeatable: 어느 환경에서도 반복 가능해야 한다.
Self-Validating: 테스트는 성공 또는 실패로 bool 값으로 결과를 내어 자체적으로 검증되어야 한다.
Timely: 테스트는 적시에 즉, 테스트하려는 실제 코드를 구현하기 직전에 구현해야 한다.

## 5. Etc

그 밖의 사항들

### 5-1. SQL

필수 사항은 아니지만 가독성 향상을 위함

#### 5-1-1. 예약어

- 예약어는 대문자 사용
→ select(❌), SELECT(👌🏻)

#### 5-1-2. 속성(Column, Attribute) & 테이블(Table, Relation)

- Snake Case
→ modify_date
- 복수형 대신 단수형 사용
→ users(❌), user(👌🏻)
- Query 에서 backquote(``) 감싸기

#### 5-1-3. Query 예시

```sql
SELECT `user`.`modify_date` FROM `my_board`.`user`;
```

### 5-2. URI

URI는 대소문자에 따라 다른 페이지로 인식하기 때문에, 필수 사항은 아니지만 범용적으로 사용되는 방식 채택

- 소문자 사용
→ Create(❌), CREATE(❌), create(👌🏻)
- Kebab Case 사용
→ create_post(❌), createPost(❌), create-post(👌🏻)

```
https://example.com/blogs/new-post
```

### 5-3. CSS

프로젝트 진행 간 유지보수 용이성에 초점

#### 5-3-1. 변수 활용

- 색상 리스트, 글자 크기 등 사이트 일관성을 유지시켜야할 항목은 변수로 지정하여 활용

#### 5-3-2. 사이즈

- 요소 크기는 가급적 px 가 아닌 **rem**(root-em) 사용
→ html 폰트 사이즈 변경 시 하위 요소 일괄 적용 가능
→ em 과 비교해 고려사항이나 유지보수 측면에서 이점

#### 5-3-3. 변수 및 rem 활용 예시

```css
@media (min-width: 768.1px) {
		/* 가로 768px 초과시 1rem == 10px  */
    html { font-size: 62.5%; }
}
@media (max-width: 768px)  {
    /* 가로 768px 이하 1rem == 8.75px  */
    html { font-size: 54.6875%; }
}

html{
    /* 배경색 */
    --bg-color-1: #715d74;
    --bg-color-2: #a08aa3;
    --bg-color-3: #d1bad4;
    --bg-color-4: #d1bad470;
    --bg-color-5: #ffffff;

    /* 글자색 */
    --txt-color-1: black;
    --txt-color-2: rgb(59, 59, 59);
    --txt-color-3: grey;
    --txt-color-4: rgb(214, 212, 212);
    --txt-color-5: white;
    --txt-color-warn: rgb(215, 68, 68);

    /* 폰트 사이즈 */
    --font-xs: 1.2rem;
    --font-sm: 1.4rem;
    --font-base: 1.6rem;
    --font-lg: 1.8rem;
    --font-xl: 2rem;
}

.article {
	font-size : var(--font-base);
}
```

## 참고

- 팀 코딩 컨벤션 정립하기
[https://log.hodol.dev/techcourse/coding-convention](https://log.hodol.dev/techcourse/coding-convention)
- 캠퍼스 핵데이 Java 코딩 컨벤션
[https://naver.github.io/hackday-conventions-java/](https://naver.github.io/hackday-conventions-java/)
- Naver JavaScript Style Guide
[https://github.com/naver/eslint-config-naver/blob/master/STYLE_GUIDE.md](https://github.com/naver/eslint-config-naver/blob/master/STYLE_GUIDE.md)
- 나만의 코딩컨벤션 작성하기
[https://jobc.tistory.com/212](https://jobc.tistory.com/212)
- 자바 코딩 가이드(파일명, 메소드, 코딩규칙)
[https://shlee0882.tistory.com/129](https://shlee0882.tistory.com/129)
- 자바 코딩 규칙
[https://myeonguni.tistory.com/1596](https://myeonguni.tistory.com/1596)
- Mapper
[https://twofootdog.github.io/Spring-DAO와-Mapper의-차이점/](https://twofootdog.github.io/Spring-DAO%EC%99%80-Mapper%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90/)