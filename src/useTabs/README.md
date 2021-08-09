# useTabs

![캡처](https://user-images.githubusercontent.com/63100352/128661589-d179b5fb-ad3e-4fa9-84c6-d0455f67f12b.PNG)

Section1 버튼을 누르면 "I'm the content of the Section 1",
Section2 버튼을 누르면 "I'm the content of the Section 2"가 나타내려면 hooks를 이용해 쉽게 만들 수 있다.

```js
const App = () => {
  const { currentItem, changeItem } = useTabs(0, content);
  return (
    <div className="APP">
      {content.map((section, index) => (
        <button onClick={() => changeItem(index)}>{section.tab}</button>
      ))}
      <div>{currentItem.content}</div>
    </div>
  );
};
```

내가 현재 선택한 content의 인덱스를 얻어 해당 메세지를 가져왔다. 즉 배열의 인덱스가 0일 때 첫번 째 요소를 가져온다.

모든 버튼은 onClick이벤트를 가지고 버튼을 누르면 `changeItem(index)`을 실행한다.
`changeItem(index)`는 index 값을 0 또는 1로 바꾸어준다.

```js
const useTabs = (initialTab, allTabs) => {
  const [currentIndex, setCurrentIndex] = useState(initialTab);
  if (!allTabs || !Array.isArray(allTabs)) {
    return;
  }

  return {
    currentItem: allTabs[currentIndex],
    changeItem: setCurrentIndex
  };
};
```
결국 currentItem의 currentIndex를 바꿔주게 되고 모든 것을 새로고침한다.
