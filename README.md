[Redux의 소개]
Redux는 JavaScript 어플리케이션에서 data-state와 UI-state를 관리해주는 도구입니다. 이는 상태적 데이터 관리가 시간이 흐름에 따라 복잡해질수도 있는 싱글 페이지 어플리케이션에서 매우 유용하게 사용됩니다. 그리고 Redux는 React 외에도 jQuery 혹은 Angular를 사용하는 어플리케이션에서도 사용 가능합니다.

React에서의 데이터흐름은 단일 방향입니다. 이 때 데이터는 트리 모양처럼 parent-child 관계를 통해 데이터를 교류하게됩니다. 그러나 컴포넌트의 개수가 많아진다면 혹은 데이터를 교류해야 하는 컴포넌트들이 parent-child 관계가 아니라면 굉장히 복잡해지게 됩니다. 직접 데이터 교류를 구현하게 될 수도 있지만, React에서 이런 구현을 시도했다간 코드 및 구조가 매우 복잡해지며 스파게티 코드가 될 위험성이 존재합니다. 이 경우 parent-child 구조를 이용하여 교류를 시도한다고 해도 복잡합니다.

때문에 React Document에서는 Flux 디자인패턴을 제시합니다. Flux 아키텍처는 시스템에서 어떠한 Action을 받았을 때, Dispatcher가 받은 Action들을 통제하여 Store에 있는 데이터를 업데이트합니다. 변동된 데이터가 있다면 View에 리렌더링합니다. 물론 View에서 Dispatcher로 Action을 보내는 것도 가능합니다.
Dispatcher는 작업이 중첩되지 않도록 해주며 어떤 Action이 Store에 있는 데이터를 처리중이라면, 다른 Action들을 대기시킵니다.

Redux는 이 Flux 아키텍처를 편하게 사용할 수 있게 해주는 라이브러리입니다. Store에서 모든 데이터를 담고, 컴포넌트끼리 직접 교류하지 않는 대신 Store를 중간자로 삼아 교류합니다. Dispatch를 통해 Stroe에 있는 데이터를 업데이트하고 Subscribe를 통해 해당 컴포넌트에서 Store에 있는 특정 데이터의 변동을 주시하다가 변동이 생기면 바로 반영합니다.

Redux에는 세 가지 원칙이 적용됩니다.
첫째, Single Source of Truth. Redux는 어플리케이션의 state를 위해 단 한개의 Store만을 사용합니다. 모든 state가 한 곳에 존재하므로 Single Source of Truth라고 합니다.
둘째, State is read-only. 어플리케이션에서 state를 직접 변경하는 것은 불가능합니다. state를 변경하는 것은 오직 Action의 Dispatch를 통해서만 가능해야 합니다. (Action은 어떤 변화가 일어나야 할지 알려주는 객체입니다.)
셋째, Changes are made with Pure Functions. 두 번째 원칙에서 설명했듯이 Redux 어플리케이션에선 state를 직접 변경하는 것을 허용하지 않습니다. 대신에 Action을 Dispatch하여 상태값을 변경하는데 이 과정에서 받아온 Action 객체를 처리하는 함수를 Reducer라고 합니다. Reducer는 순수 함수로만 작성되어야 하는데 이 때 순수 함수라는 뜻은 외부 네트워크 혹은 데이터베이스에 접근하지 않아야하고, 반환값은 오직 매개변수 값에만 의존되어야 하며 인수는 변경되지 않아야 하고 같은 인수로 실행된 함수는 언제나 같은 결과를 반환해야하며, 순수하지 않은 API호출을 하지 말아야하는 조건들을 만족하는 함수를 가리킵니다.

본 과제는 create-react-app 방식을 통해 진행해보았으며 Atom 에디터를 통해 App.js 파일을 편집했을때 웹 페이지에 코드 변화가 직접 반영되는 것을 확인할 수 있었습니다.

This project was bootstrapped with [Create React App](https://github.com/facebookincubator/create-react-app).

Below you will find some information on how to perform common tasks.<br>
You can find the most recent version of this guide [here](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md).
