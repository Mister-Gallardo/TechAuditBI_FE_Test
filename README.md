# TechAuditBI_FE_Test

## task_1
The ChildComponent is memoized in order to prevent unnecessary re-rendering.
But now this memoization doesn
1. Memoization doesn't because makeLog function is being created anew on each render of MainComponent, causing the ChildComponent to receive a new makeLog prop every time. As a result, the memoization of ChildComponent is not effective because it's receiving a new prop on each render.
2. Fixed code with useCallback:

```
import React, { Fragment, memo, useCallback } from 'react';

const MainComponent = () => {
  const makeLog = useCallback(() => console.log('hi from MainComponent'), []);

  return (
    <Fragment>
      <ChildComponent makeLog={makeLog} />
    </Fragment>
  );
};

// memoized component
const ChildComponent = memo(({ makeLog }) => (
  <button onClick={makeLog}>say Hi from ChildComponent</button>
));
```

## task_2
Rewrite this part of code using class-based components.

```
import React, { Component } from 'react';

class ClassCounter extends Component {
  componentDidMount() {
    // This code runs when the component is mounted.
    console.log('Component has mounted');
  }

  componentDidUpdate(prevProps) {
    // This code runs when the props or state of the component update.
    if (prevProps.count !== this.props.count) {
      console.log(Count has changed to: ${this.props.count});
    }
  }

  render() {
    const { count } = this.props;

    return (
      <div>Count: {count}</div>
    );
  }
}

export default ClassCounter;
```

## task_3
The answer: 
```typescript
const transformData: TransformDataFunction = (data) => { 
    const result = [];

    for (let elem of data) {
        const obj = {label: `${elem[1][1]}, ${elem[2][1]}`, value: elem[0][1]}
        result.push(obj)
    }

    return result 
}
```
## task_4
Result:
```typescript
type UserData = [string, number | string];
type UserArray = UserData[];

type TransformedData = {
    label: string;
    value: number;
};

type TransformDataFunction = (data: UserArray[]) => TransformedData[];
```
