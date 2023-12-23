> 참조 : https://ko.legacy.reactjs.org/docs/introducing-jsx.html

# JSX
JavaScript 확장 문법으로 JavaScript의 모든 기능이 포함되어 있다.
JSX는 React "엘리멘트(element)"를 생성한다.


React에서는 본질적인 랜더링 로직이 UI 로직(이벤트가 처리되는 방식, 시간에 따 state가 변하는 방식, 화면에 표시하기 위해 데이터가 준비되는 방 등)과 연결된다는 사실을 받아들입니다.


React는 별도의 파일에 마크업과 로직을 넣어 기술을 인위적으로 분리하는 대신, 둘 다 포함하는 "컴포넌트"라고 부르는 느슨하게 연결된 유닛으로 분리합니다.


React는 JSX 사용이 필수는 아니지만 대부분 JavaScript 코드 안에서 UI 관련 작업할 때 시각적으로 더 도움이 된다 생각한다. 또한 React가 더욱 도움되는 에러 및 경고 메세지를 표시할 수 있게 해준다.


# 엘리먼트 랜더링
엘리먼트는 React 앱의 가장 작은 단위로 화면에 표시할 내용을 기술합니다.


```javascript
const element = <h1>Hello, world</h1>;
```


브라우저 DOM 엘리먼트와 달리 React 엘리먼트는 일반 객체이며(Plain Object) 쉽게 생성할 수 있습니다. React DOM은 React 엘리먼트와 일치하도록 DOM을 업데이트 합니다.


##### DOM에 엘리먼트 랜더링하기
```html
<div id="root"></div>
```
이 div 안에 들어가는 모든 엘레먼트를 React DOM에서 관리하기 때문에 이것을 "루트(root)" Dom 노드라고 부릅니다.


React로 구현된 애플리케이션은 일반적으로 하나의 루트 DOM 노드가 있습니다. React를 기존 앱에 통합하려는 경우 원하는 만큼 많은 수의 독립된 루트 DOM 노드가 있을 수 있습니다.


React 엘리먼트를 렌더링 하기 위해서는 우선 DOM 엘리먼트를 ReactDOM.createRoot()에 전달한 다음, React 엘리먼트를 root.render()에 전달해야 합니다.


```javascript
const root = ReactDOM.createRoot(
  document.getElementById('root')
);
const element = <h1>Hello, world</h1>;
root.render(element);
```


##### 랜더링 된 엘리먼트 업데이트하기
React 엘리먼트는 불변객체로 생성한 이후 엘리먼트의 자식이나 속성을 변경할 수 없습니다. 엘리먼트는 특정 시점의 UI를 보여준다.


위의 내용을 바탕으로 UI를 업데이트하는 유일한 방법은 새로운 엘리먼트를 생성하고 이를 root.render()로 전달하는 것입니다.


```javascript
const root = ReactDOM.createRoot(document.getElementById('root'));

function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  root.render(element);
}

setInterval(tick, 1000);
```

위의 방식처럼 setInterval() 콜백을 이용해 초마다 root.render()를 호출합니다.


##### 변경된 부분만 업데이트
React DOM은 해당 엘리먼트와 그 자식 엘리먼트를 엘리먼트와 비교하고 DOM을 원하는 상태로 만드는데 필요한 경우에만 DOM을 업데이트합니다.


매초 전체 UI를 다시 그리지 않고 변경된 텍스트 노드만 업데이트한다.
특정 시점에 UI가 어떻게 보일지 고민하는 이런 접근법은 시간의 변화에 따라 UI가 어떻게 변화할지 고민하는 것보다 더 많은 수의 버그를 없앨 수 있습니다.


# 컴포넌트와 프롭
Components를 통해 UI를 재사용 가능한 개별적인 여러 조각으로 나누고, 각 조각을 개별적으로 살펴볼 수 있습니다.


개념적으로 컴포넌트는 JavaScript 함수와 유사하다. "props"라고 하는 임의의 입력을 받은 후, 화면에 어떻게 표시되는지를 기술하는 React 엘리먼트를 반환합니다.


##### 함수 컴포넌트와 클래스 컴포넌트

```javascript
function Welcome(props){
  return <h1>Hello, {props.name}</h1>;
}
```

컴포넌트를 정의하는 가장 간단한 것은 JavaScript 함수를 작성하는 것이다.


이 함수는 데이터를 가진 하나의 "props" (props는 속성을ㄴ ㅏ타내는 데이터) 객체 인자를 받은 후 React 엘리멘트를 반환하므로 유효한 React 컴포넌트입니다. 이러한 컴포넌트는 JavaScript 함수이기 때문에 말 그대로 "함수 컴포넌트"라고 한다.


```javascript
class Welcome extends React.Components {
  render(){
    return <h1>Hello, {props.name}</h1>;
  }
}
```

React의 관점에서 볼 때 두 가지 유형의 컴포넌트는 동일합니다.
위의 형식을 "클래서 컴포넌트"라고 한다.


##### 컴포넌트 렌더링
이전까지는 DOM 태그만을 사용해 React 엘리먼트를 나타냈다.


```javascript
function Welcome(props){
  return <h1>Hello, {props.name}</h1>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
const element = <Welcome name="World"/>;
root.render(element);
```

위의 코드에서는 다음 순서로 동작한다.
1. element로 root.render()를 호출한다.
2. React는 {name= 'World'}를 props로 하여 Welcome 컴포넌트를 호출한다.
3. Welcome 컴포넌트는 결과적으로 <h1>Hello, World</h1> 엘리먼트로 반환한다.
4. React DOM은 반환된 엘리먼트와 일치하도록 DOM을 효율적으로 업데이트한다.

// 컴포넌트의 이름은 항상 대문자로 시작한다.


##### 컴포넌트 합성
컴포넌트는 자신의 출력에 다른 컴포넌트를 참조할 수 있습니다. 이는 모든 세부 단계에서 동일한 추상 컴포넌트를 사용할 수 있음을 의미합니다. React 앱에서는 버튼, 폼, 다이얼로그, 화면 등의 모든 것들이 흔히 컴포넌트로 표현됩니다.

```javascript
function Welcome() {
  return <h1>Hello, {props.name}</h1>;
}
function App(){
  return (
    <div>
      <Welcome name="Hong" />
      <Welcome name="Sara" />
      <Welcome name="Kim" />
    </div>
  )
}
```

위와 같이 Welcome으로 여러번 랜더링하는 App 컴포넌트를 만들 수 있다.

// 아직까지 잘 모르겠다.. 실무에서 워낙 섞어 쓰다보니 javascript 기준으로 보면 구조적으로 일부 다른 것 외에 차이점을 느끼지 못하겠다. 그래도 일딴 한번 쭉 본다는 느낌으로 현타 컨트롤 하면서 해야겠다.


##### 컴포넌트 추출

```javascript
function formatDate(date) {
  return date.toLocaleDateString();
}

function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <img className="Avatar"
             src={props.author.avatarUrl}
             alt={props.author.name} />
        <div className="UserInfo-name">
          {props.author.name}
        </div>
      </div>
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}

const comment = {
  date: new Date(),
  text: 'I hope you enjoy learning React!',
  author: {
    name: 'Hello Kitty',
    avatarUrl: 'http://placekitten.com/g/64/64'
  }
};

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <Comment
    date={comment.date}
    text={comment.text}
    author={comment.author} />
);
```

위의 Comment 컴포넌트는 author(객체), text(문자열), date(날짜)를 props로 받은 후 출력합니다.


이 컴포넌트는 구성요소들이 모두 중첩 구조로 이루어져 있어서 변경하기 어려울 수 있으며, 각 구성요소를 개별적으로 재사용하기도 힘듭니다.
