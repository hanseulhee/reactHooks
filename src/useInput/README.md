# useInput


1.
```js
const App = () => {
    const name = useInput("Mr.");
    return(
        <div className="APP">
            <h1>Hello</h1>
            <input placeholder = "Name" value= {name.value} />
        </div>
    );

};
```
2.
```js
const App = () => {
    const name = useInput("Mr.");
    return(
        <div className="APP">
            <h1>Hello</h1>
            <input placeholder = "Name" {...name} />
        </div>
    );

};
```

`{...name}`은 name안에 있는 모든 것을 풀어준다. 따라서 1번을 2번과 같이 간단하게 나타낼 수 있다.


### 유효성 검증 기능

```js
  const onChange = (event) => {
    const {
      target: { value },
    } = event;
    let willUpdate = true;
    if (willUpdate) {
      setValue(value);
    }
  };
```

willUpdate는 true여서 항상 업데이트가 된다.



```js
const useInput = (initialValue, validator) => {
  const [value, setValue] = useState(initialValue);
  const onChange = (event) => {
    const {
      target: { value }
    } = event;
    let willUpdate = true;
    if(typeof validator === "function") {
      willUpdate = validator(value);
    }
    if (willUpdate) {
      setValue(value);
    }
  };
  return { value, onChange };
};

const App = () => { 
  const maxLen = value => value.length <= 10;
  const name = useInput("Mr.", maxLen);
  return (
    <div className="APP">
      <h1>Hello</h1>
      <input placeholder="Name" {...name} />
    </div>
  );
};

```

name을 이용해 useInput에  Mr와 maxLen를 넣어주었다.
maxLen는 value의 길이를 저장한다. 따라서 value의 길이가 10보다 작으면 true가 된다.
validator타입이 function이라면 willUpdate에 validator의 결과를 업로드 한다.