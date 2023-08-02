## useAxios

> useAxios

```js
import defaultAxios from "axios";
import { useEffect, useState } from "react";

const useAxios = (options, axiosInstance = defaultAxios) => {
  const [state, setState] = useState({
    loading: true,
    error: null,
    data: null,
  });

  const [trigger, setTrigger] = useState(0);

  if (!options.url) return;

  const refetch = () => {
    setState({
      ...state,
      loading: true,
    });
    setTrigger(Date.now());
  };

  useEffect(() => {
    axiosInstance(options)
      .then((response) =>
        setState({ ...state, loading: false, data: response })
      )
      .catch((error) => setState({ ...state, loading: fasle, error }));
  }, [trigger]);

  return { ...state, refetch };
};

export default useAxios;
```

> App

```js
import "./App.css";
import useAxios from "./useAxios";

function App() {
  const { loading, error, data, refetch } = useAxios({
    url: "https://yts.mx/api/v2/list_movies.json ",
  });

  console.log(data?.data?.data?.movies);

  return (
    <>
      <h1>{data && data.status}</h1>
      <button onClick={refetch} disabled={loading}>
        {loading ? "Loading..." : "다시 불러오기"}
      </button>
      <h4>{error && error}</h4>
      <ul>
        {data?.data?.data?.movies?.map((item) => {
          return <li key={item.id}>{item.title}</li>;
        })}
      </ul>
    </>
  );
}

export default App;
```
