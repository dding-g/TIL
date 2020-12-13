# 인사이드 자바스크립트

- 라이브러리
    - knockout
        - MVVM(model, view, view Model) 패턴과 템플릿을 통해 간단하게 동적 UI를 구성할 수 있게 해주는 라이브러리
    - backbone
        - client side에 간단하게 MVC패턴을 적용 시킬 수 있는 경량 프레임워크

- 자바스크립트의 핵심 개념
    - 객체
        - JS의 거의 모든 것은 객체이다. boolean, number, string, null, undefined 은 객체가 아니기 때문에 "거의" 라고 표현함. 제외한 나머지는 모두 객체임. 하지만 null, undefined를 제외한 나머지는 객체로 다룰 수 있음.
    - 함수
        - JS에서 함수도 객체로 취급한다. 일반 객체보다 조금 더 많은 기능이 있는 객체 라고 이해하면 될 듯.
    - 프로토타입
        - 모든 객체는 숨겨진 link인 `prototype`을 가진다. 이 link는 **해당 객체를 생성한 생성자의 prototype 객체를 가르킨다.** 
    - 실행 context와 closure
        - scope 관련 개념. 추후에 정리할 예정
    
--- 
JS는 클래스를 지원하지 않지만 객체지향 프로그래밍이 가능하다. 
--- 