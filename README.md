![waving](https://capsule-render.vercel.app/api?type=waving&height=200&text=Bucketlist!&fontAlign=80&fontAlignY=40&color=gradient)
<p align='center'> Web(We arE Best) : 최수정(PM), 정재현(CTO), 고관운, 박은빈, 배지원, 변지환 </p>
<p align='center'>
  <a href="[https://github.com/kyechan99/capsule-render/labels/Idea](http://ec2-13-125-143-78.ap-northeast-2.compute.amazonaws.com:8080/swagger-ui/index.html)">
     <img src="https://img.shields.io/badge/Swagger-85EA2D?style=flat&logo=Swagger&logoColor=white"/>
  </a>
</p>



## 프로젝트 주제 및 목표
- 멋쟁이 사자처럼 백엔드 스쿨 2기에서 배웠던 내용을 토대로 팀 프로젝트 진행
- 공통의 버킷리스트를 주제로 멤버를 모집하고 참여, 후기를 작성하는 Bucketlist 사이트 구현



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
![erd01](/uploads/d90016f04db5451064cea7af4b25192c/erd01.png)



## Navigation
1. [How to Use](#how-to-use)
2. [Types](#types)
3. [Color](#color)
4. [Custom Color List](#custom-color-list)
5. [Section](#section)
6. [Reversal](#reversal)
7. [Height](#height)
8. [Text](#text)
9. [Desc](#desc)
10. [Text Background](#text-background)
11. [Text Animation](#text-animation)
12. [Font Color](#fontcolor)
13. [Font Size](#fontsize)
14. [Font Align - X](#fontalign)
15. [Font Align - Y](#fontaligny)
16. [Desc Size](#descsize)
17. [Desc Align - X](#descalign)
18. [Desc Align - Y](#descaligny)
19. [Rotate](#rotate)
20. [Demo](#demo)

Any of Idea -> [Idea-Issue](https://github.com/kyechan99/capsule-render/labels/Idea) or [PR](https://github.com/kyechan99/capsule-render/pulls)

# How to Use
```
https://capsule-render.vercel.app/api?
```
Just write query parameter end of this url. Like this

Markdown:
```
![header](https://capsule-render.vercel.app/api?type=wave&color=auto&height=300&section=header&text=capsule%20render&fontSize=90)
```

HTML:
```
<img src="https://capsule-render.vercel.app/api?type=wave&color=auto&height=300&section=header&text=capsule%20render&fontSize=90" />
```

## Types
Type data makes to change Background Image.
- [wave](#wave) : default
- [egg](#egg)
- [shark](#shark)
- [slice](#slice)
- [rect](#rect)
- [soft](#soft)
- [rounded](#rounded)
- [cylinder](#cylinder)
- [waving](#waving)
- [transparent](#transparent)

Write `&type= ` on the URL
```
![header](https://capsule-render.vercel.app/api?type=slice)
```

## Color
Change Background Image!
- `&color=auto` : Proven random color. List are [here](https://github.com/kyechan99/capsule-render/blob/master/src/pallete.json)
- `&color=timeAuto` : Proven random color, but is decided by time.
- `&color=random` : Really random color. I don't know what colors are showing.
- `&color=gradient` : Proven random gradient. List are [here](https://github.com/kyechan99/capsule-render/blob/master/src/gradient.json)
- `&color=timeGradient` : Proven random gradient, but is decided by time.
- `&color=_hexcode` : default(#B897FF)
- `&color=_custom_gradient` : Custom gradient. If write as `&color=0:EEFF00,100:a82da8`, it will be converted to { 0%: 'EEFF00', 100%: 'a82da8' }. (e.g. [DEMO](https://capsule-render.vercel.app/api?type=rect&color=0:EEFF00,100:a82da8))

If you use `auto` mode. no need to change `fontColor`. 
`auto` also change fontColor auto.

```
![header](https://capsule-render.vercel.app/api?color=auto)
```
> If you use static color. Do not write '#'

> When use `timeAuto` and `timeGradient`?
>
> Used section `header` and `footer` at the same time. 

## Custom Color List
You can **customize the list of colors** that will appear randomly only for `&color=auto` and `&color=gradient`.

Write `&customColorList= ` on the URL.

- If you use `&color=auto`, look at [pallete list](https://github.com/kyechan99/capsule-render/blob/master/src/pallete.json).
- If you use `&color=gradient`, look at [gradient list](https://github.com/kyechan99/capsule-render/blob/master/src/gradient.json).

Pick the color patterns you want and remember the `idx` value.

For example, if the idx values ​​are 0, 2, and 3, write: `&customColorList=0,2,3`

If you want to make many apperances of `idx=2`, you can write them repeatedly. (e.g. `&customColorList=0,2,2,2,2,3`)

```
![header](https://capsule-render.vercel.app/api?color=gradient&customColorList=0,2,2,5,30)
```

## Theme
You can use the specified combination using `theme=`.

Even if `color` and `fontColor` are used, theme has the highest priority.

Check the list of available themes at [pallete_theme.json](https://github.com/kyechan99/capsule-render/blob/master/src/pallete_theme.json).

```
![reversal](https://capsule-render.vercel.app/api?type=rect&text=RECT&fontAlign=30&fontSize=30&desc=Use%20theme&descAlign=60&descAlignY=50&theme=radical)
```

> I'm currently adding combinations from the [Link:theme](https://github.com/anuraghazra/github-readme-stats/blob/master/themes/README.md) little by little.

## Section
Section data makes reverse Background Image.
- `&section=header` : (default)
- `&section=footer`

Write `&section= ` on the URL
```
![footer](https://capsule-render.vercel.app/api?section=footer)
```

## Reversal
Reverse the image left and right. (Color at the same time)
- `&reversal=false` : (default)
- `&reversal=true`

```
![reversal](https://capsule-render.vercel.app/api?type=slice&reversal=true&color=gradient)
```

## Height
Change Image Size. Default value is 120.

Write `&height= ` on the URL
```
![header](https://capsule-render.vercel.app/api?height=400)
```
> Do not write `px`

## Text
Input text over the Image.

Write Something `&text= `.

```
![header](https://capsule-render.vercel.app/api?text=Hello%World!)
```

> You can't use some Special Characters. Like '#', '&', '/' ... 
>
> It makes confused API

> It is recommended to use `%20` (blank) only

## Desc
Input desc over the Image.

Write Something `&desc= `.

```
![header](https://capsule-render.vercel.app/api?height=400&text=Hello%20World!&desc=Hello%20capsule%20render)
```

> You can't use some Special Characters. Like '#', '&', '/' ... 
>
> It makes confused API

> It is recommended to use `%20` (blank) only

## Text Background
Background of Text.

Write `&textBg=true` to active.

> If you want to increase background-size, 
add `%20` between text values.
This is because background-size depends on the length of the english-text. (%20 means spacing)

```
![header](https://capsule-render.vercel.app/api?type=rounded&color=gradient&text=%20asdf%20&height=300&fontSize=100&textBg=true)
```

## Text Animation
Make the text dynamic.

Write `&animation= `, if you want to use.

- `fadeIn` : fadeIn 1.2s
- `scaleIn` : scaleIn .8s
- `blink` : blink .6s
- `blinking` : blinking 1.6s
- `twinkling` : twinkling 4s

```
![header](https://capsule-render.vercel.app/api?text=capsule_render&animation=fadeIn)
```

## FontColor
Change text color. Default value is 000000.

Value should be Hex code with erased '#'

Write `&fontColor= ` behind **Text** query

```
![header](https://capsule-render.vercel.app/api?text=Hello%World!&fontColor=d6ace6)
```

## FontSize
Change text font size. Default value is 70.

Write `&fontSize= ` behind **Text** query

```
![header](https://capsule-render.vercel.app/api?text=Hello%World!&fontSize=40)
```

> Do not write `px`

## FontAlign
Change text horizontal-align (x). write number **between 0~100**

`&fontAlign= ` : Default value is 50. center of image

```
![header](https://capsule-render.vercel.app/api?text=Hello%World!&fontAlign=70)
```

## FontAlignY
Change text vertical-align (y). write number **between 0~100**

`&fontAlignY= ` : Default value is 50. center of image

```
![header](https://capsule-render.vercel.app/api?text=Hello%World!&fontAlignY=20)
```

## DescSize
Change desc font size. Default value is 20.

Write `&descSize= ` behind **desc** query

```
![header](https://capsule-render.vercel.app/api?text=Hello%World!&fontSize=40&desc=Desc&descSize=30)
```

> Do not write `px`

## DescAlign
Change desc horizontal-align (x). write number **between 0~100**

`&descAlign= ` : Default value is 50. center of image

```
![header](https://capsule-render.vercel.app/api?text=Hello%World!&fontAlign=70&desc=Desc&descAlign=20)
```

## DescAlignY
Change text vertical-align (y). write number **between 0~100**

`&descAlignY= ` : Default value is 60. center of image

```
![header](https://capsule-render.vercel.app/api?text=Hello%World!&fontAlignY=20&desc=Desc&descAlignY=40)
```

## Rotate
Usage `&rotate= `, to rotate text.

You can also use negative number.

> Recommend number arrange. ☞ `0 ~ 360`, `0 ~ -360`. 

```
![header](https://capsule-render.vercel.app/api?text=Hello%World!&fontSize=20&rotate=-30)
```

## Stroke
Change text stroke.

Write `&stroke=` behind query

Value should be Hex code with erased '#'

```
![header](https://capsule-render.vercel.app/api?type=rect&height=200&text=Stroke%20Test&fontAlign=70&stroke=00FF00)
```

> Recommended to use with `strokeWidth`.
>
> When used alone, strokeWidth defaults to 1.

## Stroke-width
Change text stroke width.

Write `&strokeWidth=` behind stroke query

Value must be greater than or equal to 0.

```
![header](https://capsule-render.vercel.app/api?type=rect&height=200&text=Stroke%20Test&fontAlign=70&stroke=00FF00&strokeWidth=3)
```

> Recommended to use with `stroke`.
>
> When used alone, stroke defaults to 'B897FF'.

# Demo <a id="demo">

## Wave <a id="wave">
![wave](https://capsule-render.vercel.app/api?type=wave&color=auto&height=200&text=WAVE)

## Egg <a id="egg">
![egg](https://capsule-render.vercel.app/api?type=egg&color=auto&height=210)

## Shark <a id="shark">
![shark](https://capsule-render.vercel.app/api?type=shark&color=gradient&height=140)

## Slice <a id="slice">
![slice](https://capsule-render.vercel.app/api?type=slice&color=auto&height=200&text=SLICE&fontAlign=70&rotate=13&fontAlignY=25&desc=desc%20function%20is%20also%20rotated.&descAlign=70.&descAlignY=44)
  
## Rect <a id="rect">
![rect](https://capsule-render.vercel.app/api?type=rect&color=gradient&text=%20%20RECT%20%20&fontAlign=30&fontSize=30&textBg=true&desc=Use%20%27textBg%27%20to%20highlight%20%27text%27&descAlign=60&descAlignY=50)

## Soft <a id="soft">
![soft](https://capsule-render.vercel.app/api?type=soft&color=auto&text=Good%20to%20use%20with%20other%20readme&fontSize=40&animation=twinkling)

## Rounded <a id="rounded">
![rounded](https://capsule-render.vercel.app/api?type=rounded&color=timeAuto&text=Rounded%20with%20stroke&fontAlignY=50&fontSize=40&height=200&stroke=000000&strokeWidth=2)

## Cylinder <a id="cylinder">
![cylinder](https://capsule-render.vercel.app/api?type=cylinder&color=auto&text=Cylinder&fontAlignY=45&fontSize=40&height=150&animation=blinking&desc=desc%20is%20also%20animated&descAlignY=70)

## Waving <a id="waving">
![waving](https://capsule-render.vercel.app/api?type=waving&height=200&text=Waving!&fontAlign=80&fontAlignY=40&color=gradient)

## Transparent <a id="transparent">
![transparent](https://capsule-render.vercel.app/api?type=transparent&fontColor=703ee5&text=Transparent&height=150&fontSize=60&desc=Only%20Use%20Text&descAlignY=75&descAlign=60)



<hr/>

# Things that helped contribute

- SVG Path Easy Maker [Codepen](https://codepen.io/kyechan99/pen/yLeQVBa)
- SVG Path draw [mavo.io](https://mavo.io/demos/svgpath/)


![footer](https://capsule-render.vercel.app/api?type=wave&color=auto&height=200&section=footer&text=Now%20Use%20me!&fontSize=90)
