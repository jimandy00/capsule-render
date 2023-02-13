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



## 📅 일정

| 날짜 | 일정 |
| --- | --- |
| 2023년 1월 13일 | 아이디어 회의 및 발표 |
| 2023년 1월 17 ~ 18일 | 서류 작성 |
| 2023년 2월 3일 | 멘토님 중간점검 |
| 2023년 1월 19일 ~ 2월  12일 | 구현 |
| 2023년 2월 13일 | 강사님 피드백 |
| 2023년 2월 16일 | 발표 및 평가 |
| 2023년 2월 17일 | 데모데이(수료) |



## 개발환경 (badge로 할까?)
- JAVA 17
- Build : Gradle 6.8
- Framework : SpringBoot 3.0.1
- DB : MySql 8.0
- Server : AWS EC2
- Deploy : Docker
- CI&CD : GitLab
- IDE : Intellij Ultimate

### 라이브러리
```java
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    implementation 'org.springframework.boot:spring-boot-starter-web'
    implementation 'org.springframework.boot:spring-boot-starter-validation'
    implementation 'org.springframework:spring-messaging:6.0.3'
    implementation group: 'org.springframework.security', name: 'spring-security-messaging', version: '6.0.1'

    compileOnly 'org.projectlombok:lombok'
    runtimeOnly 'com.mysql:mysql-connector-j'
    annotationProcessor 'org.springframework.boot:spring-boot-configuration-processor'
    annotationProcessor 'org.projectlombok:lombok'
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
    testCompileOnly 'org.projectlombok:lombok:1.18.12' // 테스트 의존성 추가
    testAnnotationProcessor 'org.projectlombok:lombok:1.18.12' // 테스트 의존성 추가

    // 캐싱 사용하기 위한 의존성
    implementation 'org.springframework.boot:spring-boot-starter-cache'

    // Image 추가를 위한 스프링 클라우드 의존성 추가
    implementation 'org.springframework.cloud:spring-cloud-starter-aws:2.2.6.RELEASE'

}
```



## ERD
![erd01](https://user-images.githubusercontent.com/114675855/218395176-3862b71f-cfdb-4c14-8fc3-b40150f780c1.png)



## 체크리스트
- [x]  주제 선정
    - 공통의 `버킷리스트` 를 주제로 멤버를 모집하는 서비스
- [x]  상세 기능
    - 게시글
        - 폼을 통해 버킷리스트를 작성하고 날짜, 지도, 이미지 추가가 가능하다.
        - 버킷리스트 게시글에서 댓글과 대댓글, 참가 신청이 가능하다.
        - 호스트는 참가 신청서를 보고 참가자를 선택할 수 있다.
        - 참가 인원이 달성되거나 모집기간이 만료되면 해당 게시글에 참여 신청이 마감된다.
        - 버킷리스트 이행이 완료되면 참가자와 버킷리스트에 대한 평점을 작성할 수 있다.
    - 채팅방
        - 참여 승인을 받은 버킷리스트의 모집기간이 만료되면 자동으로 생성된다.
        - 채팅방 나가기 기능과 강퇴 기능이 있다.
    - 마이피드
        - 본인만 확인 가능하다.
        - 작성, 좋아요, 신청, 승낙, 완료한 버킷리스트가 출력된다.
    - 프로필
        - 본인 외 로그인하지 않은 사용자까지 확인 가능하다.
        - 프로필 사진, 이메일, 평점, 리뷰가 출력된다.
        - 프로필 사진은 프로필 주인일 경우만 수정이 가능하다.
        - 프로필 주인의 평점과 리뷰를 확인할 수 있다.


