# remixProject

# 2025-01-21

# 1 BASIC

# 1.1

npx create-react-router@7.0.1 wemake

Docker를 사용하지않으니 관련된 내용 삭제하기
React Router는 하나의 프레임워크

app/routes.ts에 route를 정의하면 그건 사용자가 URL로 이동할수있는 페이지가된다.
프레임워크 사용할떈 내가 코드를 다루는게아니라 프레임워크에 맞춰야한다 -> 제어역전

# 1-2

react route해서 만든 컴포넌트는 react module이 된다.
react module은 효율적이고 멋진 방식으로 데이터를 fetch, load, mutate 할수있다.

route("/about", "potato/tomato.tsx")를 했을떄 React Router가 바로 render하는것이 아니다. 대신 root.tsx파일을 확인한다.

root.tsx파일을 보면
export default function App() {
return <Outlet />;
}

이렇게 되어있는데 이 컴포넌트는 React Router에서 import한 Outlet 컴포넌트를 return하고있어.

- outlet은 일종의 placeholder 같은 역할을 하는 component이다.
  url에 따라 componen가 무엇이 되든 그걸로 바뀔것이다. 따라서 예를들어 유저가 /about에 있으면 React Router가 tomato.tsx로 가서 default export를 가져올것이다.
  그리고 저 위에 root.tsx파일의 Outlet자리에 tomato.tsx파일의 값인 AboutUs를 넣는것이다.

React Router가 Outlet을 url에 따라 유저에게 보여줘야하는 component를 default export component로 교체한 이후에는 Layout export를 찾게된다
이 모든 레이아웃 렌더링은 root.tsx안에 있는 layout 안에 들어가게 되는것이다.

outlet의 컴포넌트 tomato.tsx는 layout의 {children}에 들어가게 된다.

layout의 좋은점은 페이지를 만들떄마다 html 전체 구조를 매번 작성하지 않아도 되기 떄문이다.

React Router가 애플리케이션의 정상동작을 처리할 뿐 아니라 오류 처리하는것도 도와주기떄문이다.
ErrorBoundary는 에러가 떳을떄 렌더링 될 component이다.

script component

1. ScrollRestoration
   ㄴ 페이지를 이동했다가 이전 페이지로 돌아갈 때, 혹은 페이지에 돌아가면 스크롤이 원래 위치에 있게한다. 페이지를돌아갈떄마다 맨위에서 시작하는건 별로임
2. Scripts
   ㄴ 우리가 브라우저에 보내는 모든 js코드임
   이 두개가 react router가 나중에 js코드로 교체할 컴포넌트들인데
