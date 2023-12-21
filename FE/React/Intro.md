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
