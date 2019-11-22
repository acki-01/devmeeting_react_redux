# Hooks

## useState

Hook `useState` is used to keep and manipulate component state:

```jsx
import React, { useState } from 'react';

const App = () => {
    const [name, setName] = useState('');

    return (
        <div>
            <p>You entered name: {name}</p>
            <input onChange={e => setName(e.target.value)} />
        </div>
    );
};
```

But you need to remember that `setState` is asynchronous.

## useEffect

The usages of this hook are:

-   Mimic `componentDidMount` and `componentDidUnmount` in class component
-   Mimic `componentDidUpdate` in class component
-   Async calls

It takes function callback inside and array with dependencies on which changes it will fire callback. Inside you can return a function which e.g. removes listeners

```jsx
import React, { useState, useEffect } from 'react';

const App = () => {
    const [name, setName] = useState('');
    // componentDidMount and componentDidUnmount
    useEffect(() => {
        console.log('Once');
        return () => {
            console.log('Cleanup');
        };
    }, []);

    // componentDidUpdate
    useEffect(() => {
        console.log(`You have typed: ${name}`);
    }, [name]);

    useEffect(() => {
        const asyncFunc = async () => await fetchData();
        asyncFunc();
    }, []);

    return (
        <div>
            <p>You entered name: {name}</p>
            <input onChange={e => setName(e.target.value)} />
        </div>
    );
};
```
