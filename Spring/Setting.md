# 스프링 환경 설정

## 1. 프로젝트 생성

- <https://start.spring.io/>에 접속

![](https://github.com/kabommm/TIL/blob/main/Spring/img/setting.PNG?raw=true)

- 위 그림을 참고하여 설정 후 GENERATE

- IntelliJ에서 생성된 파일을 open

## 2. build.gradle 설정

```
dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-data-jpa'  //Spring Data JPA
	implementation 'org.springframework.boot:spring-boot-starter-thymeleaf' //Thymeleaf
	implementation 'org.springframework.boot:spring-boot-starter-web'   //Spring Web
	implementation "com.querydsl:querydsl-jpa:${queryDslVersion}"   //
	implementation "com.querydsl:querydsl-apt:${queryDslVersion}"   //
	compileOnly 'org.projectlombok:lombok'  //Lombok
	developmentOnly 'org.springframework.boot:spring-boot-devtools' //Spring Boot DevTools
	runtimeOnly 'mysql:mysql-connector-java'    //MySQL Driver
	annotationProcessor 'org.projectlombok:lombok'  //Lombok
	testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
```

## 3. application.properties 설정

```
//Mysql 연결
spring.datasource.driver-class-name= com.mysql.cj.jdbc.Driver
spring.datasource.url= jdbc:mysql://127.0.0.1:3306/bootex?serverTimezone=Asia/Seoul&characterEncoding=UTF-8
spring.datasource.username=유저이름
spring.datasource.password=비밀번호

//JPA관련 설정
spring.jpa.hibernate.ddl-auto=update    //프로젝트 실행 시에 자동으로 DDL(create, alter, drop 등)을 생성할 것인지를 결정하는 설정.
//설정값은 create, update, create-drop, validate 등이 있음. create-매번 테이블 생성을 새로 시도, update-변경이 필요한 경우는 alter로 변경 또는 테이블이 없으면 create
spring.jpa.properties.hibernate.format_sql=true //Hibernate가 동작하면서 발생하는 SQL을 포맷팅해서 출력합니다. 실행되는 SQL의 가독성을 높여 줍니다.
spring.jpa.show-sql=true    //JPA 처리 시에 발생하는 SQL을 보여줄 것인지를 결정

//Thymeleaf
spring.thymeleaf.cache=false
```

## 4. gitignore 설청

.gitignore에 src/main/resources/application.properties 추가
