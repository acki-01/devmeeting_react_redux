# First component

Here's probably the simplest component we can write, in all it's glory:

![first component](/assets/first_component.png)

```jsx
import React from 'react';

const App = () => {
    return <h1>Hello DevMeetings!</h1>;
};

export default App;
```

It doesn't do much, but still there's a couple of things to notice:

-   `import React from 'react';` - always import React
-   `export default App;` is exported from the file

## Single product component

![single product](/assets/single_product.png)

```jsx
import React, { useState } from 'react';

const App = () => {
    const [product, setProduct] = useState({
        id: 1,
        name: 'Apple',
        price: 14.0,
        showDesc: false,
        desc: 'This is very tasty apple'
    });

    return (
        <section>
            <h1>Hello DevMeetings!</h1>
            <div>
                <header>{product.name}</header>
                <p>{product.desc}</p>
                <span>{product.price}$</span>
            </div>
        </section>
    );
};

export default App;
```

## Passing props

```jsx
<Component foo={42} bar={'Hello, Devmeetings'} />;
const Component = props => (
    <>
        <div>{props.foo}</div>
        <div>{props.bar}</div>
    </>
);
```

-   not exactly a best practice, but for now, the data is hardcoded inside of the component
-   There's plenty of elements to render, but a component must always return exactly one element or null
