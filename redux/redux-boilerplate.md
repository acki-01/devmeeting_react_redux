# Redux Boilerplate

## Reducer

Reducer is a function which has access to store and action which was made. Depending on action type decide how to handle state and returns it new version. If provided action wasn't specify in reducer function it returns unchanged state. To create basic reducer create folder `store` in `./src` directory file `storeName.js` and in it

```js
const initialState = {
    items: [],
    text: ''
};
export const storeName = (state = initialState, action) => {
    switch (action.type) {
        case 'ADD':
            return {
                ...state,
                items: [...items, action.item]
            };
        default:
            return state;
    }
};
```

In Your application there can be many reducers to create from them one store create `reducer.js` file and in it:

```js
import { combineReducers } from 'redux';
import { storeName } from './storeName';
import { storeName2 } from './storeName2';

export default combineReducers({
    storeName,
    storeName2
});
```

## Store

In `index.js`:

```jsx
import { store } from './store';
import { Provider } from 'react-redux';

ReactDOM.render(
    <Provider store={store}>
        <App />
    </Provider>,
    document.getElementById('root')
);
```

## Actions

Action is a function that provides information about what happened in application and contains data which is passed to reducer. Create file `actions.js`:

```js
export const addItem = item => ({
    type: 'ADD',
    item
});
```

## Redux devtools

Immutability of Redux gives us access to a powerfull tool in which we can inspect our store, changes and move in a timeline of actions that were dispatched.

Install Redux devtools plugin for Chrome and in application in `./src/index.js`:

```js
import React from 'react';
import { createStore, applyMiddleware, compose } from 'redux';
import { Provider } from 'react-redux';
import reducer from './reducer';
const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;

const store = createStore(
    reducer,
    window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
);

ReactDOM.render(
    <Provider store={store}>
        <App />
    </Provider>,
    document.getElementById('root')
);

export default App;
```

### Resources

-   [Redux Docs](https://redux.js.org/)
-   [Provide immutability in Redux](https://daveceddia.com/react-redux-immutability-guide/)
-   [Redux devtools](https://github.com/zalmoxisus/redux-devtools-extension/)
