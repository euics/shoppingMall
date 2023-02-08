# :paperclip: 쇼핑몰 프로젝트
> 쇼핑몰 프로젝트 with JPA (지은이 변구훈) 책을 참고하여 학습한 프로젝트

![image](https://user-images.githubusercontent.com/103410386/217541868-39c4900b-6551-4e25-b064-200a974511ae.png)

## 목차
- [들어가며](#들어가며)
  - [프로젝트 소개](#1-프로젝트-소개)    
  - [프로젝트 기능](#2-프로젝트-기능)    
  - [사용 기술](#3-사용-기술)   
     - [백엔드](#3-1-백엔드)
     - [프론트엔드](#3-2-프론트엔드)

- [구조 및 설계](#구조-및-설계)
  - [패키지 구조](#1-패키지-구조)
  - [DB 설계](#2-db-설계)

- [학습 내용](#학습-내용)


## 들어가며
### 1. 프로젝트 소개

JPA에 대한 이해도와 SpringBoot에 대한 공부를 하기 위해 쇼핑몰을 만들면서
<br>
Spring Data JPA 기본 사용법
<br>
Spring Sercurity로 구현하는 회원 서비스
<br>
이커머스 개발의 기초에 대해 학습한다.

### 2. 프로젝트 기능

- **사용자 -** Security 회원가입 및 로그인, 회원가입시 유효성 검사 및 중복 검사
- **상품 등록 및 조회 -** 등록한 대표 사진을 홈페이지 메인 화면에 보여준다.

### 3. 사용 기술

#### 3-1 백엔드

##### 주요 프레임워크 / 라이브러리
- Java 11
- SpringBoot 2.7.3
- JPA(Spring Data JPA)
- Spring Security
- Spring Validation

##### Build Tool
- Gradle

##### DataBase
- MySQL
- H2Database

#### 3-2 프론트엔드
- Html/Css
- JavaScript
- Bootstrap
- Thymeleaf


## 구조 및 설계   
   
### 1. 패키지 구조
   
<details>
  
<summary>패키지 구조 보기</summary>   
 

```
📦src
 ┣ 📂main
 ┃ ┣ 📂java
 ┃ ┃ ┗ 📂eucis
 ┃ ┃ ┃ ┗ 📂shop
 ┃ ┃ ┃ ┃ ┗ 📂config
 ┃ ┃ ┃ ┃ ┃ ┣ 📜AuditConfig.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜AuditorAwareImpl.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜WebMvcConfig.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜SecurityConfig.java
 ┃ ┃ ┃ ┃ ┣ 📂constant
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemSellStatus.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜OrderStatus.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜Role.java
 ┃ ┃ ┃ ┃ ┣ 📂controller
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemController.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜MainController.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜MemberController.java
 ┃ ┃ ┃ ┃ ┣ 📂dto
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemFormDto.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemImgDto.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemSearchDto.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜MainItemDto.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜MemberFormDto.java
 ┃ ┃ ┃ ┃ ┣ 📂entity
 ┃ ┃ ┃ ┃ ┃ ┣ 📜BaseEntity.abstract
 ┃ ┃ ┃ ┃ ┃ ┣ 📜BaseTimeEntity.abstract
 ┃ ┃ ┃ ┃ ┃ ┣ 📜Cart.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜CartItem.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemImg.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜Member.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜Order.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜OrderItem.java
 ┃ ┃ ┃ ┃ ┣ 📂repository
 ┃ ┃ ┃ ┃ ┃ ┣ 📜Cart.interface
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemImgRepository.interface
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemRepository.interface
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemRepositoryCustom.interface
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemRepositoryCustomImpl.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜MemberRepository.interface
 ┃ ┃ ┃ ┃ ┃ ┣ 📜OrderItemRepository.interface
 ┃ ┃ ┃ ┃ ┃ ┗ 📜OrderRepository.interface
 ┃ ┃ ┃ ┃ ┣ 📂service
 ┃ ┃ ┃ ┃ ┃ ┣ 📜FileService.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemImgService.java
 ┃ ┃ ┃ ┃ ┃ ┣ 📜ItemService.java
 ┃ ┃ ┃ ┃ ┃ ┗ 📜MemberService.java
 ┃ ┗ 📂resources
 ┃ ┃ ┣ 📂static
 ┃ ┃ ┃ ┣ 📂css
 ┃ ┃ ┃ ┃ ┣ 📜layout1.css
 ┃ ┃ ┣ 📂templates
 ┃ ┃ ┃ ┣ 📂fragments
 ┃ ┃ ┃ ┃ ┣ 📜footer.html
 ┃ ┃ ┃ ┃ ┗ 📜header.html
 ┃ ┃ ┃ ┣ 📂item
 ┃ ┃ ┃ ┃ ┣ 📜itemDtl.html
 ┃ ┃ ┃ ┃ ┣ 📜itemForm.html
 ┃ ┃ ┃ ┃ ┗ 📜itemMng.html
 ┃ ┃ ┃ ┣ 📂layouts
 ┃ ┃ ┃ ┃ ┗ 📜layout1.html
 ┃ ┃ ┃ ┣ 📂member
 ┃ ┃ ┃ ┃ ┣ 📜memberForm.html
 ┃ ┃ ┃ ┃ ┗ 📜memberLoginForm.html
 ┃ ┃ ┃ ┣ 📜main.html
 ┃ ┃ ┗ 📜application.properties
 ┃ ┃ ┗ 📜application-test.properties
 ```
  
 </details>   
 <br/>    
   
     
 ### 2. DB 설계

![image](https://user-images.githubusercontent.com/103410386/217539558-06cfaadf-fd3c-428f-bd9e-432999c5ae21.png)
   
<br/>

## 학습 내용
<br>
https://blog.naver.com/eucis/222997310638
