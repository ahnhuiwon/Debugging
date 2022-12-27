## `require() of ES modules is not supported - axios.`

### 발견

node js를 aws에 업로드하여 node server.js 명령어로 실행하던중 axios관련 에러가 발생하였다.

```
  |   | ... require() of ES modules is not supported.
  |   | ... Error [ERR_REQUIRE_ESM]: Must use import to load ES Module: /app/node_modules/axios/index.js
  |   | ... 
  |   | ... ^
  |   | ... throw new ERR_REQUIRE_ESM(filename, parentPath, packageJsonPath);
  |   | ... internal/modules/cjs/loader.js:1172
```

<br />

#### 원인?

이 버그의 원인은 해당 버전의 axios가 require()을 지원하지 않기 때문이다라는 글이 대부분이었다.

좀 더 알아보면서 확실한 원인이 나온다면 다시 github에 정리해두겠다.

<br />

### `해결 방법`

github 글 중 axios의 버전을 낮춰서 사용하면 이 문제를 해결한다는 글이 있어 시도해서 해결하였다.

```
npm install axios@0.27.2
```
