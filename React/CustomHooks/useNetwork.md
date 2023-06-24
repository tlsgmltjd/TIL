## useNetwork

```js
const useNetwork = (onChange) => {
  const [status, setStatus] = useState(navigator.online);
  const handleChange = () => {
    setStatus(navigator.online);
    onChange(navigator.online);
  };

  useEffect(() => {
    window.addEventListener("online", handleChange);
    window.addEventListener("offline", handleChange);

    return () => {
      window.removeEventListener("online", handleChange);
      window.removeEventListener("offline", handleChange);
    };
  }, []);

  return status;
};
```
