## React-hook-form

- [contorlled / uncontrolled component](https://github.com/tlsgmltjd/TIL/blob/main/React/style.md)

- **제어 컴포넌트** : state를 사용하여 폼과 실시간으로 값이 동기화된다.
  > 하지만 불필요한 렌더링 + state가 늘어나 유지보수가 어려워진다.
- **비제어 컴포넌트** : React에 의해 값이 제어되지 않는 컴포넌트
  > 실시간 유효성 검사, 조건부 제출 버튼 비활성화 등 X

### react-hook-form 을 사용한다면

- 비제어 컴포넌트의 장점은 그대로 살리면서 제어 컴포넌트의 기능까지 가능하게 해준다!
- 폼을 다루는 코드도 간결해진다!

```
npm i react-hook-form
```

### 사용

```js
import { useForm } from "react-hook-form";

function Page() {
  const {
    register,
    handleSubmit,
    watch,
    setError,
    setValue,
    formState: { errors, isSubmitting, isDirty, isValid },
  } = useForm({ mode: "onChange" });
}
```

- `register` : 입력 요소를 폼과 연결하여 유효성을 확인하고 input 태그를 다룰수 있다.

  - `register`의 첫 번째 매개변수로 name을 주고 두 번째 값으론 유효성을 검사할 `options` 객체가 들어간다.
  - `...register("email", {required: { vlaue : true, message: "필수!!" }})`
    > value와 message로 구성된 객체를 주어 에러 메세지를 제공할 수 있다!

- `handleSubmit` : 폼의 `onSubmit` 속성에 사용한다. (인자로는 실행될 함수를 받는다)
- `watch` : 실시간으로 입력폼에 적힌 값을 확인하는 옵션
- `setValue` : 폼 필드의 값을 변경한다.
  - `setValue("firstName", "John")`
    > firstName 필드의 값을 John으로 설정할 수 있다.
- `formState` : 전체 폼에 대한 정보를 포함한다.
  > ex) error

```ts
import React from "react";
import { useForm } from "react-hook-form";

function MyForm() {
  const { register, handleSubmit, setError, setValue } = useForm();

  const onSubmit = (data) => {
    if (data.password.length < 5) {
      return setError("너무 짧아요!");
    }

    console.log(data);
    setValue("email", ""); // email 필드 지우기
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("firstName")} placeholder="First Name" />
      <input {...register("lastName")} placeholder="Last Name" />
      <input
        {...register("email", {
          required: { value: true, message: "필수!!!!" },
        })}
        placeholder="Email"
      />
      <input
        {...register("password", {
          required: { value: true, message: "필수!!!!" },
        })}
        placeholder="Password"
      />

      <button type="submit">Submit</button>
    </form>
  );
}
```
