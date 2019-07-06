---
layout: post
title: Spring Overview
image: /img/library.png
published: false
date: '2019-07-06'
---
## 스프링 프레임워크 오버뷰
버전 5.1.8.RELEASE
목차
1. 왜 "Spring"인가?
2. 스프링과 스프링 프레임워크의 역사
3. 설계 철학
4. 피드백 및 프로젝트 기여 방법
5. 시작방법

스프링은 자바 엔터프라이즈 어플리케이션을 쉽게 만들 수 있게 합니다. 엔터프라이즈 환경에서 자바 언어를 적용하기 위한 모든 것을 제공합니다. 그루비와 코틀린과 같은 JVM의 대안 언어들 또한 지원합니다. 그리고 어플리케이션의 요구사항에 의존하는 다양한 아키텍쳐를 생성할 수 있는 유연성을 가지고 있습니다. 스프링 프레임워크 5.1에서 스프링은 JDK SE 8 이상, JDK 11 LTS에 대한 추가 지원을 제공합니다.
스프링은 많은 어플리케이션 시나리오의 범주를 지원합니다. 큰 사업에서 어플리케이션은 오랜 시간동안 사용될 수 있고 개발자의 컨트롤 하에 JDK와 어플리케이션 서버에서 실행되어야 합니다. 혹은 클라우드 환경과 같이 임베디드된 서버와 하나의 jar 파일로 실행될 수도 있습니다. (예를 들어, 배치 혹은 병합 프로그램 등의 서버가 필요없는 경우)
스프링은 오픈소스입니다. 다양한 실제 유스 케이스를 기반으로 지속적인 피드백을 제공하는 크고 활발한 커뮤니티를 가지고 있습니다. 이 점은 스프링을 오랜 시간 성공적으로 발전할 수 있도록 하는 원동력입니다. 

1. 왜 "스프링"인가?

> "스프링"은 다른 문맥에서 다른 의미를 같습니다. 스프링의 모든 시작점이 되는 스프링 프레임워크 자체를 의미하기도 합니다. 시간이 흐르면서 다른 스프링 프로젝트가 스프링 프레임워크 위에 개발되었습니다. "스프링"이라고 하는 것은 보통 프로젝트의 전체를 의미합니다. 이 레퍼런스 문서는 스프링 프레임워크 자체에 집중하였습니다.

스프링 프레임워크는 모듈로 분할됩니다. 어플리케이션은 필요한 모듈을 선택할 수 있습니다. 코어 컨테이터의 모듈은 configuration model과 dependency injection mechanism을 포함하고 있습니다. 이는 메시징과 trnasactional data, persistence과 웹 등으로 다른 어플리케이션 아키텍처를 지원합니다. 서블릿 기반의 스프링 MVC 웹 프레임워크와 병렬적으로 스프링 웹플럭스 reactive web framework 또한 제공합니다.

모듈에 대한 간단한 설명 : 스프링의 프레임워크 jar 파일은 JDK 9의 모듈 path ("Jigsaw")에서 배포되어야 합니다. Jigsaw에 배포가능한 어플리케이션 내에서 사용하기 위해 스프링 프레임워크 5는 jar 파일을 "Automativ-Module-Name" manifest entries라는 안전한 언어 레벨의 모듈 이름 ("spring.core", "spring.context" 등)을 jar 아티팩트 이름과 독립적으로 사용합니다. (jar 파일은 "." 대신에 "-"을 사용하는 동일한 네이밍 패턴을 적용합니다. 예를 들면 "spring-core"과 "spring-context"). 물론 스프릉의 프레임워크 jar는 JDK 8과 9이상의 버전의 classpath에서 잘 작동합니다.

2. 스프링의 역사와 스프링 프레임워크

> 스프링은 J2EE 스펙의 복잡성에 대응하기 위해 2003년에 만들어졌습니다. Java EE과 스프링에 경쟁을 부추기기도 했지만, 사실 스프링은 Java EE에서도 사용가능합니다. 스프링 프로그래밍 모델은 Java EE 플랫폼 스펙을 적용하지 않았습니다. 대신 EE unbrella의 개별적인 스펙과 통합하였습니다.

- Servlet API (JSR 340)
- WebSocket API (JSR 356)
- Concurrency Utilities (JSR 236)
- JSON Binding API (JSR 367)
- Bean Validation (JSR 303)
- JPA (JSR 338)
- JMS (JSR 914)

또한 transaction을 고려한 JTA/JCA 셋업에서도 작동합니다.
스프링 프레임워크는 Dependency Injection (JSR 330)과 Common Annotations (JSR 250) 스펙을 지원합니다. 개발자는 해당 스펙을 지원하는 대안 프레임워크를 사용할 수도 있습니다. 
스프링 프레임워크 5.0에서 스프링으 Java EE 7를 최소 스펙으로 정의하였습니다. (Servelet 3.1+, JPA 2.1+) - 새로운 API와의 통합을 사용하려면 Java EE 8 런타임 환경(Servlet 4.0, JSON Binding API)이 필요합니다. 따라서 스프링은 Tomcat 8-9, WebSphere 9, JBoss EAP 7과 완벽하게 호환가능합니다.
시간이 흐름에 따라 어플리케이션 개발에서 Java EE의 역할은 진화하고 있습니다. 초창기 Java EE와 스프링은 어플리케이션을 서버에 배포하기 위해 생성해야 했습니다. 오늘날에는 스프링 부트의 도움으로 어플리케이션은 데브옵스, 클라우드 친화적인 방법으로 생성할 수 있습니다. 임베디드된 서블릿 컨테이너를 약간 수정하면 가능합니다. 스프링 프레임워크 5에서는 웹 플럭스 어플리케이션은 서블릿 API를 직접적으로 사용하지 않고 네티와 같은 서블릿 컨테이너가 아닌 서버 위에서 실행할 수 있습니다. 
스프링은 지속으로 혁신하고 진화합니다. 스프링 프레임워크 상에서 스프링 부트, 스프링 시큐리티, 스프링 데이터, 스프링 클라우드, 스프링 배치 등의 다른 프로젝트들이 있습니다. 각 프로젝트는 각자의 코드 레파지토리, 이슈 트래커, 릴리즈 카덴스를 가지고 있습니다. spring.io/projects 에서 스프링 프로젝트의 전체 리스트를 보세요.

3. 설계 철학

프레임워크에 대해 배울 때 어떻게 하는지 뿐만 아니라 따라야할 원칙 또한 알아야 합니다. 다음은 스프링 프레임워크의 원칙 가이드입니다.
모든 수준에서 선택을 제공하라. 스프링은 설계 결정을 가능한 마지막에 할 수 있도록 합니다. 예를 들어 코드 변경 없이 configuration을 통해 persistence 제공자를 변경할 수 있습니다. 다른 인프라 

Accommodate diverse perspectives. Spring embraces flexibility and is not opinionated about how things should be done. It supports a wide range of application needs with different perspectives.

Maintain strong backward compatibility. Spring’s evolution has been carefully managed to force few breaking changes between versions. Spring supports a carefully chosen range of JDK versions and third-party libraries to facilitate maintenance of applications and libraries that depend on Spring.

Care about API design. The Spring team puts a lot of thought and time into making APIs that are intuitive and that hold up across many versions and many years.

Set high standards for code quality. The Spring Framework puts a strong emphasis on meaningful, current, and accurate javadoc. It is one of very few projects that can claim clean code structure with no circular dependencies between packages.

4. Feedback and Contributions
For how-to questions or diagnosing or debugging issues, we suggest using StackOverflow, and we have a questions page that lists the suggested tags to use. If you’re fairly certain that there is a problem in the Spring Framework or would like to suggest a feature, please use the GitHub Issues.

If you have a solution in mind or a suggested fix, you can submit a pull request on Github. However, please keep in mind that, for all but the most trivial issues, we expect a ticket to be filed in the issue tracker, where discussions take place and leave a record for future reference.

For more details see the guidelines at the CONTRIBUTING, top-level project page.

5. Getting Started
If you are just getting started with Spring, you may want to begin using the Spring Framework by creating a Spring Boot-based application. Spring Boot provides a quick (and opinionated) way to create a production-ready Spring-based application. It is based on the Spring Framework, favors convention over configuration, and is designed to get you up and running as quickly as possible.

You can use start.spring.io to generate a basic project or follow one of the "Getting Started" guides, such as Getting Started Building a RESTful Web Service. As well as being easier to digest, these guides are very task focused, and most of them are based on Spring Boot. They also cover other projects from the Spring portfolio that you might want to consider when solving a particular problem.

Version 5.1.8.RELEASE
Last updated 2019-06-13 13:44:59 UTC