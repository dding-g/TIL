# 한 줄 짜리 unique 값 생성 코드
```
const uid = () => Date.now().toString(36) + Math.random().toString(36).substr(2);
```

