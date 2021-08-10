# useClick


### useRef
reference란 component의 어떠한 부분을 선택할 수 있는 방법이다. (= document.getElementById())
React의 모든 component는 reference element를 가지고 있다.


### useClick

```js
import React, { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom";

const useClick = (onClick) => {
  const element = useRef();
  useEffect(() => {
    if (element.current) {
      element.current.addEventListener("click", onClick);
    }
    return () => {
      if (element.current) {
        element.current.removeEventListener("click", onClick);
      }
    };
  }, []);
  return element;
};

const App = () => {
  const sayHello = () => console.log("say hello");
  const title = useClick(sayHello);

  return (
    <div className="APP">
      <div>hi</div>
      <h1 ref={title}>Hi</h1>
    </div>
  );
};
```
useClick으로 click에 따라서 console창에 문구를 다르게 넣는 것을 만들었다.