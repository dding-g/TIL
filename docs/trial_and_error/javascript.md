## Javascript Event

- 이벤트 핸들러는 모든 브라우저에서 이벤트를 동일하게 처리하기 위한 이벤트 래퍼 SyntheticEvent 객체를 전달받습니다. stopPropagation() 와 preventDefault()를 포함해서 인터페이스는 브라우저의 고유 이벤트와 같지만 모든 브라우저에서 동일하게 동작합니다.

- SyntheticEvent는 풀링됩니다. 성능상의 이유로 SyntheticEvent 객체는 재사용되고 모든 속성은 이벤트 핸들러가 호출된 다음 초기화됩니다. 따라서 비동기적으로 이벤트 객체에 접근할 수 없습니다.

- 주의
    - 비동기적으로 이벤트 속성을 참조하고 싶다면 이벤트 객체의 event.persist() 를 호출하세요. 합성 이벤트 풀에서 제거되고 사용자의 코드에서 참조가 가능해집니다.

~~따라서 event handler는 async 로 처리 되면 안된다. 해당 비동기 작업이 끝나지 않으면 이벤트도 끝나지 않으므로   `SyntheicEvent` 객체가 반환 될 수 없기 때문에 다음 이벤트를 처리하는데 지장이 있다. 따라서 이벤트 핸들러에 비동기 구문을 넣을 때는 주의해야한다.~~ 

**~~해당 비동기 구문을 호출하기 전에 `event.persist()` 로 이벤트를 반환해야한다.~~**

**수정 : `e.persist()` 는 비동기 처리 이후에 이벤트 객체를 참조해야 할 때 사용된다.**

```
function onClick(event) {
  console.log(event); // => nullified object.
  console.log(event.type); // => "click"
  const eventType = event.type; // => "click"

  setTimeout(function() {
    console.log(event.type); // => null
    console.log(eventType); // => "click"
  }, 0);

  // 동작하지 않습니다. this.state.clickEvent 은 null만 가지게 될 것입니다.
  this.setState({clickEvent: event});

  // 이벤트 속성을 추출할 수 있습니다.
  this.setState({eventType: event.type});
}
```

---
