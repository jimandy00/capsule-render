![waving](https://capsule-render.vercel.app/api?type=waving&height=200&text=Bucketlist!&fontAlign=80&fontAlignY=40&color=gradient)
<p align='center'> Web(We arE Best) : 최수정(PM), 정재현(CTO), 고관운, 박은빈, 배지원, 변지환 </p>
<p align='center'>
  <a href="http://ec2-13-125-143-78.ap-northeast-2.compute.amazonaws.com:8080/swagger-ui/index.html">
     <img src="https://img.shields.io/badge/Swagger-85EA2D?style=flat&logo=Swagger&logoColor=white"/>
  </a>
  <a href="https://ringed-suggestion-46f.notion.site/ceff928e9f1f4e2482f07387b997f593">
      <img src="https://img.shields.io/badge/Notion-000000?style=flat&logo=Notion&logoColor=white"/>
  </a>
  <a href="https://www.ourbucketlist.link">
    <img src="https://img.shields.io/badge/link-Bucketlist-green?logo=data">
  </a>
</p>



## 프로젝트 주제 및 목표

- 멋쟁이 사자처럼 백엔드 스쿨 2기에서 배웠던 내용을 토대로 팀 프로젝트 진행
- 공통의 버킷리스트를 주제로 멤버를 모집하고 참여, 후기를 작성하는 Bucketlist 사이트 구현

## 일정

| 날짜 | 일정 |
| --- | --- |
| 2023년 1월 13일 | 아이디어 회의 및 발표 |
| 2023년 1월 17, 18일 | 프로젝트 문서화 작업 |
| 2023년 2월 3일 | 멘토님 중간점검 |
| 2023년 1월 19일 ~ 2월  12일 | 구현 |
| 2023년 2월 13일 | 강사님 피드백 |
| 2023년 2월 16일 | 발표 및 평가 |
| 2023년 2월 17일 | 데모데이(수료) |

## EndPoint

[endpoint](https://www.notion.so/endpoint-681884ecf7fe4f37b658c5fcbb1a6ed3)

## 개발환경(badge로꾸며버릴지도몰라)

- JAVA 17
- Build : Gradle 6.8
- Framework : SpringBoot 3.0.1 (JPA, Query DSL), Spring security(Email, OAuth)
- DB : MySql 8.0, AWS RDB
- Server : AWS EC2, S3, Docker
- CI&CD : GitLab
- IDE : Intellij Ultimate
- Front-End : JS, HTML, CSS, JQuery, Axios

### 라이브러리

```java
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    implementation 'org.springframework.boot:spring-boot-starter-web'
    implementation 'org.springframework.boot:spring-boot-starter-validation'
    implementation 'org.springframework:spring-messaging:6.0.3'
    implementation group: 'org.springframework.security', name: 'spring-security-messaging', version: '6.0.1'

    compileOnly 'org.projectlombok:lombok:1.18.20'
    runtimeOnly 'com.mysql:mysql-connector-j'
    annotationProcessor 'org.springframework.boot:spring-boot-configuration-processor'
    annotationProcessor 'org.projectlombok:lombok:1.18.20'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
    implementation 'org.springframework.security:spring-security-test'
    // swagger
    implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.0.2'

    //SNS로그인을 위한 의존성
    implementation 'io.jsonwebtoken:jjwt:0.9.1'
    implementation 'org.springframework.boot:spring-boot-starter-security'
    implementation 'org.springframework.boot:spring-boot-starter-oauth2-client:3.0.1'
    implementation group: 'javax.xml.bind', name: 'jaxb-api', version: '2.3.1'

    //== 이메일 인증을 위한 의존성 시작 ==//
    implementation 'org.springframework.boot:spring-boot-starter-mail:3.0.1'
    //== 이메일 인증을 위한 의존성 끝 ==//

    //chat 관련 의존성
    implementation 'org.springframework.boot:spring-boot-starter-websocket'
    implementation group: 'com.google.code.gson', name: 'gson', version: '2.10'
    implementation 'org.webjars:sockjs-client:1.5.1'
    implementation 'org.webjars:stomp-websocket:2.3.4'
    implementation group: 'com.fasterxml.jackson.core', name: 'jackson-databind', version: '2.14.1'
    implementation 'org.springframework.boot:spring-boot-starter-thymeleaf:3.0.1'

    //querydsl(스프링 부트 3.0 이상)
    implementation 'com.querydsl:querydsl-jpa:5.0.0:jakarta'
    annotationProcessor "com.querydsl:querydsl-apt:${dependencyManagement.importedProperties['querydsl.version']}:jakarta"
    annotationProcessor "jakarta.annotation:jakarta.annotation-api"
    annotationProcessor "jakarta.persistence:jakarta.persistence-api"

    // test에서 사용할 springframework 라이브러리 의존시킴
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
    testCompileOnly 'org.projectlombok:lombok:1.18.20' // 테스트 의존성 추가
    testAnnotationProcessor 'org.projectlombok:lombok:1.18.20' // 테스트 의존성 추가

    // 캐싱 사용하기 위한 의존성
    implementation 'org.springframework.boot:spring-boot-starter-cache'

    // Image 추가를 위한 스프링 클라우드 의존성 추가
    implementation 'org.springframework.cloud:spring-cloud-starter-aws:2.2.6.RELEASE'

    // 정적 파일 빌드 안하고 바로 반영할 수 있는 기능 추가
    implementation 'org.springframework.boot:spring-boot-devtools:3.0.2'
}
```

## GIT FLOW

### 인프라(이 부분을 어쩌면 좋을까 🤔)

- [ ]  AWS 서버
    - 
- [ ]  Swagger
    - API 문서 자동화 용이 및 API 테스트 기능
- [ ]  GitLab CI&CD pipeline 구축
    - 소프트웨어 버전 관리 및 테스트 기능
    - git의 project가 업데이트 되었다면, 현재 컨테이너 제거 후 재실행 하도록 [deploy.sh](http://deploy.sh) 작성
    - docker file을 통해 build
    - crontab 기능으로 정정기적으로 [deploy.sh](http://deploy.sh) 실행

## ERD(재현님이랑 상의해서 다시 짜야됨)

![erd01.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1a20b0e7-2661-4b8e-b0d6-b757ce63abcc/erd01.png)

## ERROR CODE

| 도메인 | 에러코드 | 설명 |
| --- | --- | --- |
|  | DUPLICATED_EMAIL | 중복됩니다. |
|  | DUPLICATED_USERNAME | userName이 중복됩니다. |
|  | DUPLICATED_ALARM | 알람이 중복됩니다. |
|  | INCORRECT_PASSWORD_CORRECT | Email이 중복됩니다. |
|  | INVALID_PASSWORD | 패스워드가 잘못되었습니다. |
|  | USERNAME_NOT_FOUNDED | 해당 사용자는 없습니다. |
|  | REFRESH_TOKEN_NOT_FOUNDED | 해당 사용자에 대한 리프레시 토큰이 없습니다. |
|  | INVALID_TOKEN | 잘못된 토큰입니다. |
|  | INVALID_REFRESH_TOKEN | refresh token 만료 |
|  | INVALID_PERMISSION | 사용자가 권한이 없습니다. |
|  | POST_NOT_FOUND | 해당 포스트가 없습니다. |
|  | COMMENT_NOT_FOUND | 해당 댓글이 없습니다. |
|  | DUPLICATED_LIKE | 같은 글에 좋아요를 두 번 눌렀습니다. |
|  | DATABASE_ERROR | DB에러 |
|  | REVIEW_NOT_FOUND | 해당 리뷰가 없습니다. |
|  | BUCKETLIST_NOT_FOUND | 해당 버킷리스트가 없습니다. |
|  | APPLICATION_NOT_FOUND | 해당 신청서가 없습니다. |
|  | ALARM_NOT_FOUND | 해당 알람이 없습니다. |
|  | FILE_NOT_EXISTS | 빈 파일입니다. |
|  | EXCEED_ENTRANT_NUM | 참가자 수를 초과하였습니다. |
|  | FILE_UPLOAD_ERROR | 파일 업로드에 실패했습니다. |
|  | WRONG_FILE_FORMAT | 파일 형식이 틀립니다. |
|  | PROFILE_NOT_FOUND | 해당 프로필이 없습니다. |
|  | CHAT_ROOM_NOT_FOUNT | 채팅방을 찾을 수 없습니다. |

## 기능리스트

- [ ]  게시글
    - 전체 게시글, 카테고리별 게시글 확인 가능
    - 폼을 통해 버킷리스트를 작성하고 날짜, 지도(카카오맵 API), 이미지 추가
    - 버킷리스트 게시글에서 댓글과 대댓글, 참가 신청이 가능
    - 호스트는 참가 신청서를 보고 참가자를 선택
    - 참가 인원이 달성되거나 모집기간이 만료되면 해당 게시글에 참여 신청이 마감
    - 버킷리스트 이행이 완료되면 참가자와 버킷리스트에 대한 평점을 작성
- [ ]  채팅방
    - 참여 승인을 받은 버킷리스트의 모집기간이 만료되면 자동으로 생성
    - 채팅방 나가기와 강퇴 기능
- [ ]  마이피드
    - 본인만 확인 가능
    - 작성, 좋아요, 신청, 승낙, 완료한 버킷리스트가 출력
- [ ]  프로필
    - 본인 외 로그인하지 않은 사용자까지 확인 가능
    - 프로필 사진, 이메일, 평점, 리뷰가 출력
    - 프로필 사진은 프로필 주인일 경우만 수정이 가능
    - 프로필 주인의 평점과 리뷰를 확인
- [ ]  회원가입, 로그인
    - 네이버, 구글 API를 사용한 로그인
- [ ]  알람
    - 신규 댓글, 버킷리스트 참가 신청, 리뷰 실시간 알림
- [ ]  검색/필터링
    - 검색 기능
    - 일정, 가격 필터링 기능
- [ ]  테스트 코드
    - 테스트

## UI 개발

[템플릿](https://themes.iamabdus.com/star/2.2/index.html)

- [ ]  홈
    - 홈 화면으로 이동하는 로고, 채팅방 회원가입, 로그인, 검색 기능이 포함된 헤더와 푸터
    - 회원가입, 로그인 모달
    - 홈화면 카테고리
    
    ![screencapture-ourbucketlist-link-2023-02-14-15_06_49.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d9f3924f-c13c-49b8-bcf5-f29d1fc2c630/screencapture-ourbucketlist-link-2023-02-14-15_06_49.png)
    
    ![screencapture-ourbucketlist-link-2023-02-14-15_06_59.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ffd0ba61-8992-4635-90ff-5bcd498756cf/screencapture-ourbucketlist-link-2023-02-14-15_06_59.png)
    
- [ ]  버킷리스트
    - 날짜, 가격 별로 필터링
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/84c2c767-625a-46f9-99a0-b48fdf18d31a/Untitled.png)
    
- [ ]  포스트
    - 폼을 통한 게시글 작성
    - 제목, 일자, 위치 등 버킷리스트 정보, 지도, 사진
    - 버킷리스트 참가 신청, 댓글 작성
    
    ![게시글 작성](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4169b27e-2012-4499-afcd-2287929eee88/screencapture-ourbucketlist-link-post-createform-2023-02-14-15_18_56.png)
    
    게시글 작성
    
    ![작성된 게시글](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/177689f0-5b61-49de-bcd4-360b990afe15/screencapture-ourbucketlist-link-post-88-2023-02-14-15_09_51.png)
    
    작성된 게시글
    
- [ ]  채팅
    - 버킷리스트 호스트와 참여자에게 자동 생성되는 채팅방
    
    ![screencapture-ourbucketlist-link-chat-room-2023-02-14-16_19_20.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/86ab2153-d691-427a-bdec-b5af7f3ff819/screencapture-ourbucketlist-link-chat-room-2023-02-14-16_19_20.png)
    

- [ ]  알람
    - 로그인하면 댓글, 게시물 상태에 따른 알림 확인 가능
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cb04871e-180d-4150-b51c-3a25ea8d126e/Untitled.png)
    

- [ ]  마이피드
    - 작성한, 좋아요한, 신청한, 승낙받은, 완료한 버킷리스트 확인
    
    ![신청한 버킷리스트 클릭한 모습](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fb7847de-7123-4900-a1e6-dac58495b7e8/screencapture-ourbucketlist-link-my-2023-02-14-17_06_44.png)
    
    신청한 버킷리스트 클릭한 모습
    
- [ ]  마이페이지
    - 프로필 사진, 유저 이름, 유저 이메일, 평점, 리뷰 출력
    
    ![screencapture-ourbucketlist-link-profile-19-2023-02-14-17_07_29.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1267dff3-05e2-45ac-b138-c71222e8b7e3/screencapture-ourbucketlist-link-profile-19-2023-02-14-17_07_29.png)
    

## 개선해야할 부분

## WEEKLY LOG

| 회차 | 주소 |
| --- | --- |
| 1주차 | https://gitlab.com/S2uJeong1/bucketlist/-/tree/main/Weekly_Log @January 20, 2023 11:45 AM |
| 2주차 | https://gitlab.com/S2uJeong1/bucketlist/-/tree/main/Weekly_Log |
| 3주차 | https://gitlab.com/S2uJeong1/bucketlist/-/blob/main/Weekly_Log/%5B3%EC%A3%BC%EC%B0%A8%5Didea_9%ED%8C%80_%EC%A7%84%ED%96%89%EC%83%81%ED%99%A9_%EA%B3%B5%EC%9C%A0.md |
| 4주차 | https://gitlab.com/S2uJeong1/bucketlist/-/blob/main/Weekly_Log/%5B4%EC%A3%BC%EC%B0%A8%5Didea_9%ED%8C%80_%EC%A7%84%ED%96%89%EC%83%81%ED%99%A9_%EA%B3%B5%EC%9C%A0.md |
| 5주차 |  |
