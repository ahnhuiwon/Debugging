## `React Uncaught ReferenceError: process is not defined`

### `발견`

node js 패키지 cheerio를 활용한 할인 스크랩 웹 사이트를 만들 계획을 세웠고 

옛날에 제작하다 말았던 react 프로젝트를 사용하던 중 코드 변경시

React Uncaught ReferenceError: process is not defined이란 에러와 함께 화면 전체를 iframe이 막고있어서

클릭등 어떠한 행동도 먹히지 않았다.
  
<br />

#### `원인?`

이 버그의 원인을 요약하면 다음과 같다.

react-error-overlay 패키지가 원인인데 이 패키지의 존속성은 webpack v5를 지원하도록 업데이트 되었고

react-scripts v4와 호환되지 않는것이 원인이다.

(검색해보니 webpack5는 NodeJS 전역 'process'의 자동 polyfill을 제거하며, 이는 process fallback을 빈 객체로 추가한다고 한다. )

<br />

### `해결 방법`

package.json에 다음 코드를 추가한다.

```

"resolutions": {
    "react-error-overlay": "6.0.9"
},

"scripts":{
    "preinstall": "npx npm-force-resolutions",
    ....
},

"devDependencies":{
    "react-error-overlay": "6.0.9",
...
}

```

<br />

1. package.json에 있는 의존성들의 특정 버전이나 range를 지정할 수 있다. react-error-overlay의 버전을 6.0.9로 지정한다.

2. preinstall은 패키지를 설치하기 전에 실행하는 코드이다. npm은 npm-force-resolutions 패키지를 사용해 사용하는 라이브러리의 하위 모듈 버전을 고정해야한다.

3. devDependencies 개발 환경시에 사용하는 의존성이다. 1번과 react-error-overlay의 버전을 6.0.9로 지정한다.

