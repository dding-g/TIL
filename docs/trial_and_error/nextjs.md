## error - ReferenceError: regeneratorRuntime is not defined
- 원인은 잘 모르겠으나, `.babelrc` 파일의 plugins에 `["@babel/plugin-transform-runtime"]` 을 추가하여 해결.
- 구글링을 하다보니 `@babel/pollyfill` 도 같이 검색이 됐는데, 어떤건지는 정확히 잘 모르겠음. 는 [요기](trial_and_error/javascript?id=polyfill폴리필-이란)에 pollyfill 에 대한 내용 정리함.
- 참고 문헌
    - [babel document](https://babeljs.io/docs/en/babel-plugin-transform-runtime)
    - [babel/pollyfill 등에 대한 글](https://programmingsummaries.tistory.com/401)
