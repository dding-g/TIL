## HTMLElement Dataset
`e.target.dateset` 과 같이 `HTMLElement.dataset` 을 사용하는 경우 명명 규칙이 있다.

```jsx
<component 
	data-id="id" 
	data-pageId="pageId" 
/>
```

위 예시에서 id는 명명 가능하지만 대문자가 들어간 pageId 는 명명이 불가능 하다.

[HTMLElement.dataset 예시](https://developer.mozilla.org/ko/docs/Web/API/HTMLElement/dataset)

```jsx
<component 
	data-id="id" 
	data-page-id="pageId" 
/>
```

이런식으로 정의했을때, `javascript` 에서는 `pageId` 로 key 를 가져 올 수 있다. (대쉬, 점, 콜론 다음에 오는 건 카멜 케이스로 치환되어서 정의된다.)

