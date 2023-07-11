## React Query

- 💡 fetching, caching, 서버와의 실시간 데이터 동기화를 지원해주는 라이브러리이다!

```
npm install @tanstack/react-query
```

### 사용방법

- `QueryClient` 의 인스턴스르 만들어 감싸준 `QueryClientProvider` 에 `client` Props로 인스턴스를 넘겨준다.

```js
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.tsx";

import { QueryClient, QueryClientProvider } from "@tanstack/react-query";

const queryClient = new QueryClient();

ReactDOM.createRoot(document.getElementById("root") as HTMLElement).render(
  <React.StrictMode>
      <QueryClientProvider client={queryClient}>
        <App />
      </QueryClientProvider>
  </React.StrictMode>
);
```

### 캐싱

- ReactQuery의 장점 중 하나는 데이터를 캐싱한다는 것이다.
  > 불러온 데이터의 복사본을 저장하여 이후 동일한 데이터 요청에 재접근 속도를 줄인다.

#### ReactQuery가 데이터를 불러오는 경우

1. 브라우저에 포커스가 들어온 경우
2. 새로운 컴포넌트 마운트가 발생한 경우
3. 네트워크 재연결이 발생한 경우

### 데이터 가져오기

- `useQuery` 훅을 사용하여 데이터를 가져오는 경우이다.

```js
const { data, isLoading } = useQuery(["고유한 키 값!"], fetcher함수);
```

<br />

```js
import axios from 'axios'
import { useQuery } from "@tanstack/react-query";

async fuction fetchUsers() {
  const response = await axios.get(url);
  return response.data;
};

const UsersList = () => {
  // query의 고유한 키 값을 넘겨준다. -> 캐시 시스템에서 저장되고 불러오기 위해 고유한 값을 넘겨줌
  const { data, isLoading } = useQuery(["users"], fetchUsers);

  return (
    {isLoading ? "Loading..." : (
        <div>
            {data.map((user) => (
                <div key={user.id}>{user.name}</div>
            ))}
        </div>
        )
    }
  );
};
```

### DEV TOOL

```
npm install @tanstack/react-query-devtools
```

- `ReactQueryDevtools` 을 사용하면 캐시된 데이터와 쿼리 상태를 시각적으로 확인할 수 있다.

```js
import { ReactQueryDevtools } from "react-query/devtools";

function App() {
  return (
    <>
      <Router />
      <ReactQueryDevtools />
    </>
  );
}
```

### 옵션

- `useQuery`의 세 번째 파라미터에 옵션을 추가할 수 있다.

```js
const { data } = useQuery("users", fetchUsers, { enabled: false });
```

### cacheTime

- 캐싱 시간을 설정해줄 수 있다.
  > Deafult 5분

```js
{
  cacheTime: Infinity;
}
```

> ex

```js
const { data } = useQuery("key", fetcher, {
  cacheTime: Infinity;
});
```

### staleTime

- `staleTime`을 설정해주면 그 시간만큼 백그라운드에서 데이터를 불러오지 않는다.
  > Default 0

```js
{
  staleTime: 6000;
}
```

### refetchOnMount

- `refetchOnMount`는 백그라운드에서 데이터를 불러올지 여부를 정하는 옵션이다.
  > Default true

```js
{
  refetchOnMount: false;
}
```

### refetchOnWindowFocus

- 유저가 페이지에 포커스를 했을 때 데이터를 불러올지 여부를 정하는 옵션이다.
  > Default true

```js
{
  refetchOnWindowFocus: false;
}
```

### enabled

- 처음에 데이터를 불러올지 여부를 정하는 옵션이다.

```js
{
  enabled: false;
}
```

### onSuccess, onError

- api 호출 성공, 실패시 실행시킬 것들 적을 수 있다.

```js
{
  onError: (err) => {
    alert(err.message);
  };
}
```

### select

- 불러온 데이터를 변경할 수 있다.

```js
{
    select: (data) => data.slice(0, 30),
}
```

> 데이터를 30번째까지만 return 해줌

### initialData

- 데이터의 초기값을 설정하는 옵션

```js
{
  initialData: initialUserData,
}
```
