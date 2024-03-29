---
title: "팀 프로젝트 회고 - 2.페이지 구상"
date: 2021-12-03T00:00:00+09:00
lastmod: 2021-12-13T20:24:00+09:00
hero: 
url: /yi-teamproject-log-2/
description: 
tags: [log]
menu:
  sidebar:
    name: 팀 프로젝트 후기 2
    identifier: Logs-팀 프로젝트 후기 2
    parent: Logs
    weight: 10
---


쇼핑몰로 프로젝트 주제를 결정하고, 초기에 어떤 페이지가 필요할까 고민하며 작성해본 리스트다. 회의 단계에서 제외된 내용도 있고, 시간 여유상 구현하지 못한 기능들도 있다.

## 1. 기본 페이지 구성 idea

### 1-1. 사용자

상품리스트, 상품상세, 로그인/회원가입, 결제화면, 마이페이지, 장바구니, 질문답변, 리뷰, 비회원 기능, 비밀번호 초기화, 주문취소/반품, 이용약관, about

#### 1-1-1. 메인(상품리스트)

- header, nav, main, footer 구성
- 제품 정렬 기능(인기순, 가격순, 세부조건)
- 카테고리별 구분
- 제품 재고 현황에 따라 sold out 처리 및 정렬에서 뒤로 빼기
- 페이징 처리

#### 1-1-2. 상품상세

- 제품사진, 구매옵션, 구매버튼, 제품상세, 교환반품정보, 후기, QnA(비밀글)

#### 1-1-3. 회원가입/로그인

- 일반 가입/oAuth 병행 (db 설계시 oAuth 구분용 속성 추가)
- 이메일 인증
- 자동로그인

#### 1-1-4. 결제화면

- 선택 아이템 및 금액 합계, 배송 주소지 선택, 결제 수단 , 결제(구현x, pg 테스트 api가 있을까?)
- form 전송 시 구매번호 부여

#### 1-1-5. 마이페이지

- 주문관리(주문내역, 반품/취소 현황)
- 회원정보 변경, 탈퇴
- 배송 주소지 등록(기본 배송지 + 추가 배송지, 배송지 별 닉네임)
- 내 질문/내 후기

#### 1-1-6. 장바구니

- 아이템 삭제, 추가
- 로그인 전/후 장바구니 연동(쿠키 or 세션 활용)

#### 1-1-7. 리뷰

- 각 상품 페이지에 리뷰 탭 배치
- 이름은 * 처리(김*수)
- 구매번호가 있어야 후기 작성이 가능하도록
- 댓글, 좋아요, 별점
- 사진 업로드(포토리뷰, 일반리뷰) - 파일 용량 리사이즈

#### 1-1-8. 질문 답변

- 각 상품 페이지에 질문 답변 탭 배치
- 비밀글 작성 기능

#### 1-1-9. 비회원 기능

- 결제 화면, 주문현황 조회, 반품/취소

#### 1-1-10. 비밀번호 초기화

- secure random
- 메일 발송

#### 1-1-11.  주문 취소 / 반품

- 배송 상황에 따라 취소/반품 구분
- 취소요청, 요청사유

#### 1-1-12. 이용약관, 개인정보 처리 방침

- 표준양식 구해서 실제 사이트와 같은 로직으로 구현

#### 1-1-13. about(프로젝트 소개)

- 구성원, 기능 소개 등 간결한 1페이지 구성

### 1-2. 관리자

상품 등록, 재고관리, 배송관리, 매출보고, 회원관리, 질문, 반품 취소 관리, 리뷰 관리

#### 1-2-1. 상품 등록

- 아이템 번호, 분류, 아이템명, 상세 페이지, 환불교환 정보, 수량(초기 입고량)
- 상세 페이지 용 텍스트 에디터 필요(사진 업로드, html tag whistlist 지정)

#### 1-2-2. 재고 관리

- 아이템별 수량 변경
- 제품 발송처리시 -1, 취소 +1, 반품/환불은 검수 후 수기처리

#### 1-2-3. 배송 관리

- 발주 들어온 품목들 표시
- 배송현황, 운송장 입력
- 엑셀 일괄입력 기능

#### 1-2-4. 매출 보고(가능하다면)

- 일자별 매출 추이, 취소 현황, 재구매율 등

#### 1-2-5. 회원 관리

- 회원 리스트 조회
- cvs 내려받기
- 비밀번호 초기화 메일 발송 등

#### 1-2-6. 질문 관리

- 전체 질문답변 표시
- 답변/미답변 표시, 필터링
- 답변 작성/수정

#### 1-2-7. 리뷰 관리

- 전체 리뷰 표시
- 답변/미답변 표시, 필터링
- 답변 작성/수정
- 답변 일괄 작성 기능(템플릿)

#### 1-2-8. 반품 취소 관리

- 요청 정보 표시
- 처리현황 체크(상태 변경)

## 2. 추가 기능 idea

- 색상별 상품 정렬(배경제거, 색상 점유% db 저장, 유사도 높은 순으로 정렬)
- 다중조건 검색(카테고리, 가격 등)
- 인기검색어
- 연관 상품(다른 사용자가 함께 본 제품, 로그 & 트리거 & 이력 없을 경우 기본값 설정 )
- 뉴스레터
- 검색어 자동완성(로그&트리거, 키워드 빈도 순 정렬, 일부 표출, char 핸들링!)
- 포인트 적립 + 출석포인트 + 메일링 포인트
- 기타 보안 관련 기능(패스워드 암호화)
- SEO 대응