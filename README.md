## Description
Easy to use global store for React, using hooks. 

## Usage

Create a reactive hook:
```javascript
import reactive from "./reactive";

const useABC = reactive({
  a: "a",
  b: "b",
  c: "c",
  docs: [
    { id: 1, name: "joe" },
    { id: 2, name: "marry" }
  ],
  changeABC() {
    this.a = this.b = this.c = parseInt(Math.random() * 100, 10);
  },
  changeName() {
    this.docs[1].name = "xxxx";
  }
});
```

When any of the above fields, or nested fields changes, all components that use those fields will re-render.
```javascript
const Component1 = () => {
  const { a, b, c, changeABC } = useABC();
  return (
    <div>
      Component1: {a}, {b}, {c}
      <button onClick={changeABC}>Click to change ABC</button>
    </div>
  );
};


const Component2 = () => {
  const { a, b, c, docs, changeName } = useABC();
  return (
    <div>
      Component2: {a}, {b}, {c}
      {docs.map((doc, i) => (
        <div key={i}>name: {doc.name}</div>
      ))}
      <button onClick={changeName}>change name</button>
    </div>
  );
};
```
