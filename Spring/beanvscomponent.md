# @Component와 @Bean

위 내용을 알기전에 Spring이 스프링 컨테이너에 Bean들을 어떻게 생성하는지 알아보자

스프링부트 프로젝트를 만들면 가장 상위 클래스인 …Application에 @SpringBootApplication이라는

어노테이션이 있을 것이다. 그 어노테이션을 구현한 코드를 보면

![j](https://github.com/tedsoftj1123/Backend_study/blob/main/images/%08main.png)

@ComponentScan이라는게 있는데 이 어노테이션이 해당 클래스의 하위 클래스들을 스캔해서 @Component 어노테이션이나 stereotype(@Service, @Controller, @Repository 등) 어노테이션이 부여된 class를 찾아 자동으로 Bean으로 등록해주는 역할을 한다. 하위 클래스들을 스캔하기 때문에 이 어노테이션이 최상위 클래스에 붙어있는 것이다.

## @Component

기본적으로 Beane들은 싱글톤 패턴의 특징을 가지는데 이 어노테이션이 Bean들을 생성해주는 역할을 한다.

@Scope("Prototype")어노테이션을 붙여서 싱클톤 패턴이 아닌 빈을 생성할 수 도 있다.

ex) 많이 쓰이는 퍼사드 패턴을 사용할때 퍼사드 클래스에 @Component를 사용해 특정 서비스에 위 객체를 DI하고 사용함

## @Bean

위 어노테이션은 개발자가 컨트롤이 불가능한 외부 라이브러리들을 Bean으로 등록할 때 사용한다.

`@Bean`
은 메소드 레벨에서 선언하며, 반환되는 객체(인스턴스)를 개발자가 수동으로 빈으로 등록하는 어노테이션이다.

ex) 많이 쓰이는 `PasswordEncoder` 는 @Bean어노테이션을 이용해 사용한다.
