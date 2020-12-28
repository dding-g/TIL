# setState 와 immer

먼저 아래 코드를 보자.
```
this.setState(produce(draft => {
    draft.order = 3;
}))
```

위 코드는 `immer.js` 를 활용해서 우리의 `state` 를 손 쉽게 바꾸어 주는 코드이다.
위 코드가 이해 갔다면 아래 코드를 읽어보고 이해해 보자.

```
const { order } = this.state; // order : 1

this.setState(produce(draft => {
    draft.order = 3;
}), () => {
    console.log(order); // ??
})
```

위 코드에서 우리는 `state.order`를 `immer`를 이용해 변경한 후 해당 값을 console 로 찍어주었다. 이때 출력되는 값은 1 일까 3 일까?
> 
js 는 object를 다룰 때 call by referece 성질을 가지므로, 3이 호출되야 하는게 맞지 않을까?
> 
정답은 `1` 이다.
> 
js가 기본적으로 call by referece 성질을 가지고 state는 object이기 때문에 state object의 프로퍼티인 order는 state 내부 값을 따라가는게 맞다. 요컨데,
```
const { order } = this.state;
console.log(order) // 같은 값
console.log(this.state.order) // 같은 값
```
위 내용이 성립한다는 뜻 이다.
> 
아니 그러면 처음에 말했던 문제에서 왜 답은 3이 아니라 1 일까?
> 
답은 `immer.js` 안에 있다.
> 
immer는 불변성을 관리하기 위해 나온 라이브러리다. 불변성은 *해당 객체가 변하지 않는다* 는걸 보장해주는데, 우리의 `state` 도 똑같이 변하지 않는 불변의 성질을 가진다. 따라서 우리는 `this.state.order = 3` 이런식으로 접근해서 `state` 를 변경 할 수 없다. 
> 
`immer.js` 없이 이전에 우리는 어떻게 `state` 값을 바꾸었는지 알아보자.

```jsx
const { order } = this.state; // order : 1

this.setState({order: 3,}, () => {
    console.log(order); // ??
})
```

이떄의 console 값은 1 일까 3 일까? 
> 
정답은 `3` 이다. 아니 아까랑 똑같이 setState를 사용해서 바꾸었는데 왜 아까는 바뀐값으로 console이 찍히지 않았을까? 
> 
** `immer.js` 는 이전 `state` 값과 바뀐 `state` 값을 비교해서 바뀐 값 만 수정한 후, 새로운 `state` 객체로 바꿔치기한다. **