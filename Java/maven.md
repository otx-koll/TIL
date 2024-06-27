# Maven

자바용 프로젝트 관리 도구이다. 프로젝트를 빌드, 패키지, 배포 등의 역할을 수행하고 각종 라이브러리들을 관리 해주는 도구이다.

## 설정파일

### setting.xml
- 메이븐 설치시 기본으로 제공되는 xml (MAVEN_HOME/conf 디렉토리에 위치)
- 메이븐 빌드 툴과 관련한 설정파일

> 위치는 `USER_HOME/.m2/repository`에 있는데 settings.xml에 원하는 로컬 저장소의 경로를 지정 및 변경할 수 있다.

### pom.xml
- 자바 프로젝트를 빌드 툴로 메이븐을 설정하면 pom.xml이 생성된다.
- 프로젝트에 필요한 라이브러리를 정의하는 공간
  - 해당 라이브러리가 작동하는데 필요한 다른 라이브러리 자동 설치

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion> <!--POM model의 버전-->
	<parent> <!--프로젝트의 계층 정보-->
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.2.4.RELEASE</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.god</groupId> <!--프로젝트를 생성하는 조직의 고유 아이디를 결정한다. 일반적으로 도메인 이름을 거꾸로 적는다.-->
	<artifactId>bo</artifactId> <!--프로젝트 빌드시 파일 대표이름 이다. groupId 내에서 유일해야 한다.Maven을 이용하여 빌드시 다음과 같은 규칙으로 파일이 생성 된다.
		artifactid-version.packaging. 위 예의 경우 빌드할 경우 bo-0.0.1-SNAPSHOT.war 파일이 생성된다.-->
	<version>0.0.1-SNAPSHOT</version> <!--프로젝트의 현재 버전, 프로젝트 개발 중일 때는 SNAPSHOT을 접미사로 사용-->
	<packaging>war</packaging> <!--패키징 유형(jar, war, ear 등)-->
	<name>bo</name> <!--프로젝트, 프로젝트 이름-->
	<description>Demo project for Spring Boot</description> <!--프로젝트에 대한 간략한 설명-->
	<url>http://goddaehee.tistory.com</url> <!--프로젝트에 대한 참고 Reference 사이트-->

	<properties>
	<!-- 버전관리시 용이 하다. ex) 하당 자바 버전을 선언 하고 dependencies에서 다음과 같이 활용 가능 하다.
	<version>${java.version}</version> -->
		<java.version>1.8</java.version>
	</properties>

	<dependencies> <!--dependencies태그 안에는 프로젝트와 의존 관계에 있는 라이브러리들을 관리 한다.-->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-tomcat</artifactId>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
			<exclusions>
				<exclusion>
					<groupId>org.junit.vintage</groupId>
					<artifactId>junit-vintage-engine</artifactId>
				</exclusion>
			</exclusions>
		</dependency>
	</dependencies>

	<build> <!--빌드에 사용할 플러그인 목록-->
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>
```

### Life Cycle

메이븐은 프레임워크이기 때문에 미리 정의하고 있는 빌드 순서가 있는데 이를 라이프 사이클이라고 한다.

@@@ 사진

- Default(Build) : 소스코드를 컴파일 해주는 단계. 컴파일이 성공하면 target/classes 폴더가 만들어지고 컴파일 된 class 파일이 생성된다.
- Clean : 빌드 후 생성된 target을 삭제한다.
- Validate : 프로젝트가 올바른지 확인하고 필요한 모든 정보를 사용할 수 있는지 확인하는 단계
- Compile : 프로젝트의 소스코드를 컴파일 하는 단계
- Test : 유닛(단위) 테스트를 수행 하는 단계(테스트 실패시 빌드 실패로 처리, 스킵 가능)
- Pacakge : 실제 컴파일된 소스 코드와 리소스들을 jar, war 등등의 파일 등의 배포를 위한 패키지로 만드는 단계, target 디렉터리를 만든다.
- Verify : 통합 테스트 결과에 대한 검사를 실행하여 품질 기준을 충족하는지 확인하는 단계
- Install : 패키지를 로컬 저장소에 설치하는 단계, Pacakge와 다른 점은 로컬 저장소에 있는 다른 프로젝트 들이 접근이 가능하다.
- Site : 프로젝트 문서와 사이트 작성, 생성하는 단계
- Deploy : 만들어진 package를 원격 저장소에 release 하는 단계

> 복잡한 프로젝트나 멀티 프로젝트의 경우엔 Gradle이 많이 사용된다고 한다.

## 설치

- ubuntu version : 22.04

패키지 목록 업데이트
```bash
sudo apt update
```
Maven 설치
```bash
sudo apt insatll maven -y
```
버전 확인
```bash
mvn --version
```
제거
```bash
sudo apt remove maven -y
```

### wget으로 설치

wget으로 설치하면 Maven의 최신버전을 다운받을 수 있다.

- Maven 홈페이지를 방문하여 아래 사진의 빨간 네모 부분을 마우스 우클릭하여 링크 복사

@@@ 사진

아래 명령어로 다운로드
```bash
wget https://dlcdn.apache.org/maven/maven-3/3.9.8/binaries/apache-maven-3.9.8-bin.tar.gz
```
다운로드 끝나면 압축 풀기
```bash
tar -xvzf apache-maven-3.9.8-bin.tar.gz
```


## Reference

https://goddaehee.tistory.com/199

https://code-killer.tistory.com/115

https://chucoding.tistory.com/62