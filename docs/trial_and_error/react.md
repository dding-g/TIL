## Function Component 이름이 소문자 이면?

`React Hook "useDispatch" is called ~~~~~ which is neither a React function component or a custom React Hook function react-hooks/rules-of-hooks`

- `useDispatch` 라는 React hook이 `funtion component`, 이나 `custom React Hook` 도 아닌 일반 function 이나 다른 곳에서 호출 되었을 때 나오는 에러. 

- 나는 분명히 react 컴포넌트에서 호출하고 있었는데 왜 이런가 봤더니 react component 이름의 첫글자가 소문자... 

- 컴포넌트 이름이 대문자가 아니면 컴포넌트라고 인식을 못하는 듯 하다. class component 같은 경우에는 extends를 명시적으로 해주어서 괜찮을 것 같지만 function 컴포넌트는 따로 해주는게 없으니 첫글자 대문자를 보고 인식하나보다.