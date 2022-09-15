# Wanted Pre-Onboarding 6차 10팀 TenKeyLess, thingsflow 기업과제

<br>

> ## 프로젝트 개요
>
> Angular-cli 레포지토리의 issue를 보여주는 App.

<br/>

> ## 사용기술
>
> <br/>

<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=white">
<img src="https://img.shields.io/badge/react-61DAFB?style=for-the-badge&logo=react&logoColor=white">
<img src="https://img.shields.io/badge/typescript-3178C6?style=for-the-badge&logo=typescript&logoColor=white">
<img src="https://img.shields.io/badge/styled-components-DB7093?style=for-the-badge&logo=styled-components&logoColor=white">

<br>

### 해당 기술 선택이유<br>

- React

  - 생태계가 넓고, 다양한 라이브러리 사용 가능
  - virtual DOM을 활용하여 빠른 렌더링 가능
  - 단방향 데이터 바인딩을 통한 디버깅 용이

- typescript : 명시적인 정적 타입 지정을 통해 컴파일 단계에서 오류를 미리 감지할 수 있다.

- Styled-component : css를 컴포넌트화 하여 사용할 수 있다.

<br/>

> ## 폴더 구조

```
src
 ┣ api
 ┃ ┣ axios.tsx
 ┃ ┗ issueApi.tsx
 ┣ components
 ┃ ┣ Header.tsx
 ┃ ┣ Loading.tsx
 ┃ ┗ MarkdownRenderer.tsx
 ┣ pages
 ┃ ┣ Detail
 ┃ ┃ ┗ Detail.tsx
 ┃ ┣ Error
 ┃ ┃ ┗ Error.tsx
 ┃ ┗ Issue
 ┃ ┃ ┣ IssueItem
 ┃ ┃ ┃ ┗ IssueItem.tsx
 ┃ ┃ ┗ Issue.tsx
 ┣ styles
 ┃ ┣ GlobalStyle.tsx
 ┃ ┗ theme.tsx
 ┣ App.tsx
 ┣ AppContext.tsx
 ┣ Router.tsx
 ┗ index.tsx
```

> ## 기능별 설명 / Best Practice

### Context API

- isuueList와 setIssueListData 를 context 객체에 관리하여, 전역에서 해당 값에 접근할 수 있도록 구현

<br/>

### 페이지

1. 이슈 목록 화면

- 이슈 목록 API 호출 후 렌더링
  - api 호출시 쿼리를 붙여 “open 상태의 이슈” 중 “코멘트가 많은 순”으로 정렬된 데이터 호출함.
- 인피니티 스크롤 ( 화면을 아래로 스크롤 할 시 이슈 목록 추가 로딩 )
  - scroll 위치와 브라우저 크기를 계산하여 다음 데이터를 호출함.
- 데이터 요청 중 로딩 표시 스피너

<br/>

2. 이슈 상세 화면

- 마크다운 라이브러리를 통한 렌더링

<br/>

### 반응형

- grid와 % , rem을 이용한 화면 비율에 맞는 크기 조절

  </details>

<br>

> ## Git

- ### [Git branch 전략](https://github.com/wanted-pre-onboarding-fe-6-10/I.M.LAB/wiki/Git-branch-%EC%A0%84%EB%9E%B5)

- ### [커밋 컨벤션](https://github.com/wanted-pre-onboarding-fe-6-10/I.M.LAB/wiki/%EC%BB%A4%EB%B0%8B-%EC%BB%A8%EB%B2%A4%EC%85%98)

<br>

> ## Prettier, Eslint

- ### Prettier

```javascript
{
  "printWidth": 100,
  "tabWidth": 2,
  "arrowParens": "avoid",
  "singleQuote": true,
  "endOfLine": "auto"
}
```

- ### Eslint

```javascript
{
  "parser": "@typescript-eslint/parser", // eslint를 typescript에서 쓸 수 있도록 변환해줌
  "extends": ["react-app", "plugin:@typescript-eslint/recommended", "plugin:prettier/recommended"],
  "plugins": ["@typescript-eslint", "prettier"],
  "ignorePatterns": ["node_modules/"],
  "env": {
    "browser": true,
    "node": true
  },
  "rules": {
    "prettier/prettier": ["error", { "endOfLine": "auto" }],
    "no-var": "warn", // var 금지
    "no-multiple-empty-lines": "warn", // 여러 줄 공백 금지
    "no-console": ["warn", { "allow": ["warn", "error"] }], // console.log() 금지
    "eqeqeq": "warn", // 일치 연산자 사용 필수
    "dot-notation": "warn", // 가능하다면 dot notation 사용
    "no-unused-vars": "warn", // 사용하지 않는 변수 금지
    "react/destructuring-assignment": "warn", // state, prop 등에 구조분해 할당 적용
    "react/jsx-pascal-case": "warn", // 컴포넌트 이름은 PascalCase로
    "react/no-direct-mutation-state": "warn", // state 직접 수정 금지
    "react/jsx-no-useless-fragment": "warn", // 불필요한 fragment 금지
    "react/no-unused-state": "warn", // 사용되지 않는 state
    "react/jsx-key": "warn", // 반복문으로 생성하는 요소에 key 강제
    "react/self-closing-comp": "warn", // 셀프 클로징 태그 가능하면 적용
    "react/jsx-curly-brace-presence": "warn" // jsx 내 불필요한 중괄호 금지
  }
}

```

<br>

> ## 회고

### 전지현

1.  api 명세서 충분한 숙지 부족<br/>
    api 명세서를 잘 파악하지 못한 채 진행을 해서 나중에 코드를 많이 수정해야 했다.<br/>
    앞으로는 사용하기 전에 어떤 api 요청을 할 수 있는지 등을 먼저 파악한 후 진행해야 할 것이다.

    <br/>

2.  동료학습을 통한 사고 확장<br/>
    무한스크롤 구현 방법이 내가 알고 있던 방법뿐 아니라 여러 방법이 있었다. <br/>
    나의 사고에만 갇혀있지 않기 위해 코드를 공유하는 것에 대한 중요성을 느꼈다.
