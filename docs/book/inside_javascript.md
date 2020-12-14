# 인사이드 자바스크립트

## 라이브러리
- knockout
    - MVVM(model, view, view Model) 패턴과 템플릿을 통해 간단하게 동적 UI를 구성할 수 있게 해주는 라이브러리
- backbone
    - client side에 간단하게 MVC패턴을 적용 시킬 수 있는 경량 프레임워크

## 자바스크립트의 핵심 개념
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

## null과 undefined
 - js에서 `null`과 `undefined`는 다르다. `null`은 개발자가 명시적으로 값이 비어있을음 나타내고, `undefined`는 변수에 아무런 값도 할당 되지 않았다는걸 의미한다.
 - 그렇기 때문에 `typeof`로 값을 검사할 때, `null`은 결과가 `Object`로 표기된다. 따라서 `typeof`가 아닌 `===`(일치 연산자)를 활용해서 변수 값을 직접 확인해야한다.

## 자바스크립트 참조 타입 (객체)
- js에서 객체는 단순히 `이름(key):값(value)` 형태의 프로퍼티를 저장하는 컨테이너로서, 해시(Hash)라는 자료구조와 상당히 유사하다. js에서 기본 타입은 하나의 값 만을 가지지만, 참조 타입인 객체는 여러개의 property들을 포함할 수 있다.
    
## 객체
- java에서는 클래스를 정의하고, 클래스의 인스턴스를 생성하는 과정에서 객체가 만들어 지지만, js에서는 클래스라는 개념은 없고, 객체 리터럴이나 생성자 함수 등 별도의 생성 방식이 존재한다.
- 객체 생성 방법
    1. 기본 재공 Object() 객체 생성자 함수를 이용
        - ```
        var foo = new Object();
        foo.name = 'foo';
        ```
    2. 객체 리터럴 이용
        - ```
        var foo = {
            name : 'foo',
            age : 30
        };
        ```
    3. 생성자 함수 이용

- 객체 프로퍼티 삭제
    - `delete` 이용해 제거 가능
    - ```
    var foo = {
            name : 'foo',
            age : 30
        };
    delete foo.name; // name 프로퍼티 삭제
    delete foo; // not working. 객체 삭제는 불가. delete는 프로퍼티만 삭제함.
    ```

- 객체 참조 및 비교
    - ```
    var obj1 = {
        val : 40
    };
    var obj2 = obj1;
    var obj3 =  {
        val : 40
    };
    
    obj2.val = 50; // 이 때 obj1 값은?
    
    console.log(obj1 == obj2); // 결과값 (1)
    console.log(obj2 == obj3); // 결과값 (2)
    ````
        - 위 예시에서 `obj1`의 val 값은 50이다. 객체를 참조 하였기 때문에 `obj1, obj2` 는 같은 주소의 객체를 참조하고 있다. 따라서 둘 중 하나만 변경되어도 같이 변경된다.
        - 비교하였을 때 결과값은, 결과값 (1)은 true, (2)는 false이다. (==)동등 연산자는 기본 값의 경우 (숫자 등) 값 자체를 비교하지만, 객체를 비교할 경우 값 자체를 비교하는게 아닌 주소값을 비교하기 때문에 내부 값이 같아도 false 가 된다.


