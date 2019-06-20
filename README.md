# __Hooks Reference Sheet__

## The State Hook

example of using an state hook and and example of doing the same thing with a class to see the difference: https://reactjs.org/docs/hooks-state.html 

useState() returns a pair: the current state value and the function that lets you update it. You can use set multiple states and use your own set function for states and set your initial values in useState().

similar to this.setState in classes except it doesn't merge the old and new states together

__Single state functional component example:__

```
import React, { useState } from 'react';

function Example() {
    const [count, setCount] = useState(0);

    return (
        <div>count</div>
    );
}
```
__Multiple states in a functional component:__
```
import React, { useState } from 'react';

function Example() {
    const initialState = {
        count: 0,
        foo: 'bar',
        bool: false,
    }

    const [state, setState] = useState(initialState)

    return (
        <div>state.count, state.foo</div>
    );
}
```

## The Effect Hook 
https://overreacted.io/a-complete-guide-to-useeffect/

example of using an effect hook and and example of doing the same thing with a class to see the difference: https://reactjs.org/docs/hooks-effect.html

useEffect() serves the same purpose as lifecycle components for classes such as componentDidMount, componentWillMount, and componentDidUpdate.

Effects are declared inside the component so they have access to it's props and state

__Using the effect hook similarly to componentDidMount:__
```
import React, { useState } from 'react';

function Example() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        setCount(1);
    },[]);

    return (
        <div>count</div>
    );
}
```
the `[]` at the end of useEffect means it will only re-render one time on component mounting

__Using the effect hook to re-render only when a specific state is changed:__
```
import React, { useState } from 'react';

function Example() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        setCount(1);
    },[count]);

    return (
        <div>count</div>
    );
}
```
the `[count]` at the end of useEffect means it will re-render anytime the state `count` changes

__Using the effect hook to re-render when any lifecycle change happens:__
```
import React, { useState } from 'react';

function Example() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        setCount(1);
    });

    return (
        <div>count</div>
    );
}
```
the `[]` is missing this time from the effect hook, this means it will re-render when any change to lifecycle happens in your component.
