# TodayILearn
오늘 새롭게 알게된것들을 적어보자
## 0602

리액트에서 상위 컴포넌트가 하위 컴포넌트의 값을 가져오거나 변경하고 싶을때는 props를 통해서 가져오거나 변경하면 된다.

하위컴포넌트에서 상위 컴포넌트의 값에 접근하고 싶으면 event 를 통해서 접근해야한다.

## 0604
JSX를 사용할 때 싱글캐그를 닫을때는 /를 붙이지 않으면 에러가 발생한다.

## 0606

리액트에서는 state 가 바뀔때 렌더링이 발생한다. 그런데 setState를 실행하고 내부에서 아무것도 바꾸지 않는다 하더라도
리액트는 state가 변한것으로 인식한다. 그렇기때문에 렌더링이 실행되는 조건을 걸어야한다.
shouldComponentUpdate를 사용해야한다. true를 리턴하면 렌더링을 실행시키고, false를 리턴하면 렌더링이 실행되지 않는다.
혹은 상속을 받을때 Component에서 상속을 받지 않고 PureComponent에서 상속을 받으면 해결된다.

hooks에서는 memo를 사용하면 된다.

## 0613

웹 디자인을 편하게 해주는 사이트 목록
-bootstrap
-semantic-ui
-material-ui
-antdesign

## 0614
자식 컴포넌트에 props로 넘겨주는 함수는 useCallback이 필수다.

_document.js     -> html,head,body

_app.js          -> root

pages            -> 실제 컴포넌트

error.js         -> 에러발생시 화면 


