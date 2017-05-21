Live TDD 강의
======================

축구를 배울 때 이론으로 슈팅하는 방법을 배우는 것은 비효율적이라 생각합니다.
실제 축구장에 나가 강사가 슈팅하는 모습을 보며,
글로 전할 수 있는 그 이상의 배움을 얻을 수 있을 것입니다.

저는 TDD도 마찬가지라고 생각합니다.
켄트벡이 쓴 TDD 책을 읽는 것은 참 좋은 일입니다만,
책을 읽고 현장에서 바로 TDD를 적용하기는 쉽지 않을 수 있습니다.

이 강의는 마치 축구 강사가 슈팅과 패스를 몸소 보여주는 것처럼,
TDD를 통해 코드를 작성하는 것을 Live로 보여주는 강의입니다. 
물론 약간의 이론적인 내용은 배움을 더욱 풍성하게 할 것이로 생각합니다.

누군가 제게 단 하나의 실천법만을 선택하라고 강제한다면,
전 거리낌 없이 TDD(자동화된 테스트)를 선택할 것입니다.
누군가의 말처럼 TDD는 죽은 게 아니라 아직도 강력한 실천법 중 하나라 생각합니다.

서버 구동 및 확인
======================
    1. ./mvnw spring-boot:run
    2. http://localhost:8080
    화면에 Hello TDD라고 나오면 정상 구동 완료 

강의 순서
======================
## A. Hello Live TDD
### 강사 소개
    1. 전 네이버/라인/카카오 개발자
    2. 전 네이버/라인 사내 기술 강사 - TDD, 리팩토링, Legacy 코드 관련 주제
    3. 현 GGtics 창업가
    4. 2006년에 테스트 자동화 시작, 2007년부터 현재까지 TDD 실천 중
### TDD는 제가 아는 최고의 실천법
    1. 애자일, 스크럼, 페어 프로그래밍 등 한때 유행했던 많은 실천법을 시도해 봄
    2. 창업을 해보니 큰 기업에서와 같은 여유는 없어짐
    3. 극도로 실용적인 가치가 아니면 안 하게 됨
    4. 여전히 더 투자하고 싶은 실천법이 TDD + CI
### TDD의 가치
    1. 결함을 줄임 - 과학적 증명
    2. 디자인을 향상 - 경험적 가설
    3. 제 경험
        3.1. 코딩이 재밌음
        3.2. 코드를 통제하고 있는 느낌이 강화되고, 그 결과로 심리적 안정을 유지
        3.3. 실제로 결함을 안 만들고, 조기에 찾을 수 있게 함
### 이 강의의 특징
    1. 이론을 최소화
    2. 강사의 TDD, 실습, 실무 적용 토론 위주
### 좋은 초점
    1. 자바 코드, 환경 등은 모두 부가적인 것
    2. 중요한 것은 TDD의 리듬
    3. TDD로 문제 혹은 요구사항을 해결해 나가는 과정
    4. 슈팅과 패스를 눈으로 훔쳐보고 따라 하는 것처럼 보시길 추천
### 양해
    1. 자바를 안 쓴지 약 3년이 넘음
    2. 자바 코딩이 다소 서투를 수 있음
    3. 5년 전 매우 정석적인 TDD에서 현재 다소 거친 TDD를 하고 있음
    4. 최대한 정석으로 진행하려 노력
   
## B. Live TDD
### 메모 API
    1. 강사가 Spring-Boot 환경에서 메모 API TDD로 구현
    2. 중요한 단축키
        2.1. Quick Fix - 이클립스 Ctrl + 1, 인텔리J Alt + Enter
        2.2. 테스트 실행 - 이클립스 Ctrl + Alt + x - T, 인텔리J Shift + Alt + F10 - 테스트 선택
    3. 유익한 개념
        3.1. In-Out vs Out-In
        3.2. 문단, Given/When/Then
        3.3. 통합 테스트 vs 단위 테스트
        3.4. ToString Override
        3.5. Progress = 오류 국면 변환
        3.6. 한글 테스트명
        3.7. Mutation 테스트
### 메모 Repository
    1. 강사가 DB와 통신하는 Repository 통합 테스트를 TDD로 구현
    2. 유익한 개념
        2.1. 테스트 상위 클래스
        2.2. Flush & Clear
        2.3. Fixture
## C. 수강생 실습
    아래 주제 중 원하는 것을 진행
    1. 방금 만들어 본 메모 API
    2. 뉴스 시각 노출
        서비스에 아래와 같은 기준으로 시간을 노출해야 한다.
        모든 요건을 충족하도록 구현한다.
        2.1. 59분 59초를 넘지 않은 경우, 실제 서비스 시각 대신 ‘mm분 전’ 으로 노출한다.
             - 이때 분 정보가 1의 숫자일 때에는 앞에 ‘0’을 표시하지 않고 바로 분 정보를 표시한다.
             예) 3분 전 /56분 전
        2.2. 60분이 넘고 오늘 날짜인 경우, 시각정보를 노출한다.
             -오전(오후) hh:mm로 표시한다.
             -시 정보가 1의 숫자일 때에는 앞에 ‘0’을 표시하지 않고 바로 시 정보를 표시한다.
             -분 정보가 1의 숫자일 때에는 앞에 ‘0’을 함께 표시한다.
             -‘오전’ 혹은 ‘오후’ 뒤에 공백을 한칸 둔다.
             예) 오전 3:11/ 오후 11:30 / 오후 8:03
        2.3. 60분이 넘고 오늘 날짜가 아닌 경우, 날짜 정보를 노출한다.
             -YYYY.MM.DD로 표시한다.
             -달과 일이 1의 숫자일 때는 앞에 ‘0’을 함께 표시한다.
             ex) 2011.05.01
    3. 아이템-아이템 상관관계 수식
        아이템-아이템 간 얼마만큼 강한 관계가 있는지를 0.0~1.0 사이의 수로 표시한다.
        * 단, IF 문으로 풀지 말고 일반화된 수식을 도출하는 것을 목표로 한다.
        3.1. 아이템은 4가지 속성이 있다.
            - 물리 공격력(AD)
            - 마법 공격력(AP)
            - 물리 방어력(Anti-AD)
            - 마법 방어력(Anti-AP)
        3.2. 수식 정의는 스스로 한다. 아래는 예시이다.
            - corr(아이템A(AD), 아이템B(Anti-AD)) == 1
            - corr(아이템A(AD), 아이템B(Anti-AP)) == 0
            - corr(아이템A(AD, AP), 아이템B(Anti-AD)) == 0.5
            - corr(아이템A(AD), 아이템B(AD)) == 1
        
## D. 더 공부해볼 만한 주제
    1. 유지보수
        1.1. 부분적 TDD
        1.2. Cover And Modify
    2. Mock
    3. End-To-End 테스트
    4. SBE(Specification By Example)
    5. 책 추천 - TDD 익숙해지고 더 나은 환경을 만들고 싶은 분
        5.1. Growing Object-Oriented Software Guided by Tests
        5.2. Working Effectively with Legacy Code
        5.3. Specification by Example
    
## E. 토론
    1. 우리 팀에도 적용할 수 있을까?
    2. TDD는 정말 좋은 투자가 많나?    