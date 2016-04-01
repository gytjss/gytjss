JUnit
===================


**'JUnit'**이란 단위 테스트를 위한 Framework 도구이다. 
프로그램 테스트 시 디버깅을 따로 하지 않아도 되는 장점이 있어 개발 시간을 단축시킬 수 있다. **JUnit**은 테스트 결과를 Test Class로 관리하기 때문에 필요에 따라 Class를 생성하여 파일별 테스트는 물론, 히스토리 관리가 가능하다. 또한, Eclipse에 플러그 형태로 포함되어 있어서 jar을 추가하여 쉽게 사용할 수 있다.

----------

1. Assert활용하기

- assert문을 사용하여 테스트가 정상적으로 처리되도록 필요한 조건을 지정할 수 있다.
- 테스트 케이스의 수행 결과를 판별한다.
- <i class="icon-cog"></i>JDK 1.4부터 지원되는 기능이다.

- 종류
	> - fail : fail Message 지정
	> - assertArrayEquals(a, b) : 배열의 a와 b가 일치하는지 확인
	> - assertEqauls(a, b) : 객체 a와 b가 값이 일치하는지 확인
	> - assertNotNull(a) : 객체 a의 값이 Not Null인지 확인
	> - assertSame(a, b) : 객체 a와 b가 같은 객체인지 확인
	> - assertTrue(a) : 객체 a의 값이 true인지 확인

1. 어노테이션 활용하기
- java.lang.annotaion.Annotation 상속을 받는 인터페이스다.
- 일반적인 인터페이스 선언과 구분하기 위해 예약어 @를 붙인다.
- 비즈니스 로직에는 영향을 주지 않고 해당 타겟의 연결 방법이나 소스코드의 구조를 변경할 수 있다.

- JUnit에서 사용하는 어노테이션 종류
> - @Test
>  - method위에 선언되면 테스트 대상 메소드임을 의미한다.
>  - 테스트 method수행시간 제한을 둘 수 있다. 단위는 밀리세컨드이다. 
>     (ex. @Test(timeout=10000) )
>  - Exception 지정이 가능하다. (ex. @Test(expected=RuntiomException.class) )
> - @Before
>  - @Test로 지정된 method를 수행하기 전 지정된 method를 선수행한다.
> - @After
>  - @Test로 지정된 method를 수행한 후 지정된 method를 수행한다.
> - @BeforeClass
>   - @Test로 지정된 method를 수행하기 전 지정된 Class를 선수행한다.
> - @AfterClass
>    - @Test로 지정된 method를 수행한 후 지정된 Class를 선수행한다.
>>  <i class="icon-cog"></i> **@BeforeClass / @AfterClass** 로 지정된 method는 
>           **public**이면서 동시에 **static** 이어야한다.

1. 결과 확인하기
- 테스트 Class에서 오른쪽 마우스 클릭 > Run As > JUnit Test 클릭
- JUnit view에서 성공(초록) 또는 실패(빨강) 결과를 확인한다. 수행시간도 함께 확인할 수 있다.

