## Next js

- **Next.js**는 `React 라이브러리의 프레임워크`이다.

### 사용하는 이유

- **`첫 로딩시간이 길고`, `SEO에 취약한`** `CSR` 을 사용하는 React와 다르게  
  `pre-reloading`을 통해 미리 데이터가 렌더링된 페이지를 가져올 수 있다. (SSR) 사용하여 사용자 경험과 `SEO`에서도 장점을 얻을 수 있다.

- 페이지 라우팅 시스템  
  `pages` 폴더에 컴포넌트를 만들어 `export` 하면 폴더명이 페이지의 route가 된다!

  > `/products/[id]` 이렇게 dynamic route 도 사용가능하다.

- `CSR`을 사용하여 페이지간 전환  
  next는 `< Link />` 컴포넌트를 통해 페이지간의 빠르고 매끄러운 이동을 가능하게 한다.

<br />
등등 다양하다
