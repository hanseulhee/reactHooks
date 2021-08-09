# useEffect


useEffect는 componentDidMount(), componentDidUpdate(), componentWillUnMount()의 역할을 한다.

```js
const App = () => {
  const sayHello = () => console.log("Hello")
  useEffect(() => {
    sayHello();
  });
  const [number, setNumber] = useState(0);
  const [aNumber, setAnumber] = useState(0);
    
  return (
    <div className="APP">
      <div>hi</div>
      <button onClick={() => setNumber(number + 1)}>{number}</button>
      <button onClick={() => setAnumber(aNumber + 1)}>{aNumber}</button>
    </div>
  );
};
```

useEffect는 componentDidMount와 componentDidUpdate의 역할을 하기 때문에 새로고침을 하면 sayHello가 실행되기도 하고 클릭하면 sayHello가 실행되기도 한다.

useEffect는 2개의 인자를 받는데 첫번 째 인자는 function으로써의 effect다.
2번 째 인자는 만약 deps (dependency)가 있다면 effect는 deps 리스트에 있는 값일 때만 값이 변하도록 실행되게 한다.

```js
const App = () => {
  const sayHello = () => console.log("Hello");
  const [number, setNumber] = useState(0);
  const [aNumber, setAnumber] = useState(0);
  useEffect(sayHello, [number]);
  return (
    <div className="APP">
      <div>hi</div>
      <button onClick={() => setNumber(number + 1)}>{number}</button>
      <button onClick={() => setAnumber(aNumber + 1)}>{aNumber}</button>
    </div>
  );
};
```

##### dependency
useEffect는 componentDidMount와 componentWillUpdate고 number가 바뀔 때만 componentWillUpdate를 가지게 된다. component가 Mount가 되었을 때 실행시킨다.


