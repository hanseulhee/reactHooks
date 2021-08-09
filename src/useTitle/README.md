# useTitle

useTitle이란 문서 제목을 업데이트 하는 기능이다.


```js
const useTitle = (initialTitle) => {
  const [title, setTitle] = useState(initialTitle);
  const updateTitle = () => {
    const htmlTitle = document.querySelector("title");
    htmlTitle.innerText = title;
  };
  useEffect(updateTitle, [title]);
  return setTitle;
};

```
updateTitle이 mount 되면 htmlTitle은 Loading... 이 된다.



### 시간 지연 기능
```js
const App = () => {
  const titleUpdater = useTitle("Loading...");
  setTimeout(() => titleUpdater("Home"), 5000);
  return (
    <div className="APP">
      <div>hi</div>
    </div>
  );
};
```

5초의 시간을 주었다.
title은 Loading...이고 5초 뒤 Home으로 바뀌는 것을 볼 수 있다.
