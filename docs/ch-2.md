# 리액트 기본 - 클래스형 컴포넌트

## 파일 구조 살펴보기

```
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    ├── serviceWorker.js
    └── setupTests.js
```

- public/index.html: public 내부만 사용(번들러가 바라보는 곳)
- src/index.js: 자바스크립트 시작점 root
- package.json: 프로젝트에 대한 정보 ⇒ 프로젝트명, 버전, 사용하는 라이브러리, 실행 스크립트, 옵션 등

## SPA(Single-Page-App)

- 하나의 HTML 파일을 이용해 동적으로 페이지를 구성
- HTML5의 history API를 사용해 URL 변경 및 페이지 전환
- `npm run start` 키워드를 이용해 구동

## JSX

- javascript syntax extension - 자바스크립트의 확장 문법(js+html)
- 리액트에서 필수적으로 사용해야 하는 것은 아님
- createElement를 쉽게 활용(babel을 이용해 변환)
- 컴포넌트의 여러 형제가 있다면 최상위 부모로 감싸줘야 함(`<></>`)
- 자바스크립트 표현식 `{}` 사용 가능

## 컴포넌트 내보내기에 따른 불러오기 키워드

- `export default vs export { ComponentName }`
  - 이름 없이 가져올 것인지? {}를 통해 정확한 이름으로 불러올 것인지?

## 인라인 스타일 사용법

- 스타일 배열로 전달하여 사용 가능

## 리액트 스니펫 활용

- es7+ react/redux/react-native snippets

## React-icons 모듈 사용

- `npm install react-icons`

## props와 state

- props: 부모에서 자식 컴포넌트로 데이터를 전달 하는 방법
- 읽기 전용으로 자식 컴포넌트에서는 변하지 않음
- `<ChildComponent propName={value} />` 형식으로 넘기고(부모) `this.props.propName` 형식으로 받음(자식)

- state: 컴포넌트 렌더링 결과에 영향을 주는 데이터를 가진 객체
- state가 변경되면 re-render되며 state는 컴포넌트 안에서 관리
- this.state는 상태를 저장/this.setState는 상태를 업데이트(비동기)

## 리스트 관련 메서드

- 리스트를 나열할 떄는 유니크한 key 값이 필수

  - 가상 돔을 이용하는 리액트는 key를 이용해 어떤 부분이 바뀌었는지 인식
  - index는 변화할 수 있으므로 비권장

- `map()` - 배열의 모든 요소에 각각 함수를 호출한 결과를 모아 새 배열 반환
- `filter()` - 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새 배열로 반환

## 버튼 상호작용 예시

- 컴포넌트에 이벤트리스너 호출 `onClick={ () ⇒{ … } }`

## super(props)

- construtor 생성자
  - 인스턴스화 된 객체에서 다른 메서드를 호출하기 전에 수행 할 사용자 지정 초기화 제공
- super 키워드
  - 자식 클래스 내에서 부모 클래스의 생성자/메서드를 호출할 때 사용
- super 이후 this?
  - 생성자에서는 super가 하나만 사용되거나
  - this 키워드가 사용되기 전에 호출 되어야 함
- react에서 super에 props를 인자로 전달 하는 이유
  - 리액트 컴포넌트 객체가 생성 될 때 props 속성을 초기화하기 위해 props를 전달
  - 생성자 내부에서도 this.props를 정상적으로 사용하도록 보장하기 위함
