# Redux-Saga usage

To be able to use Redux-Saga in project run:
`npm install --save redux-saga axios`

Then lets create our first saga. Create folder `sagas` and in it `index.js`

```js
import { takeEvery } from 'redux-saga/effects';
import { addItem } from './actions';
function fetchItem() {
    return { name: 'Apple', amount: 1 };
}

function* getItem() {
    const item = yield call(fetchItem);
    yield put(addItem(item));
}

export function* watchSagas() {
    yield takeLatest('GET', getItem);
}
```

There are couple important methods provided bu Redux-Saga:
`takeLatest`: takes last action of its type and cancel others

`put`: use it to call an action (**without parentesis**)

`call`: use it to call a function (**with parentesis**)

To make sagas work modify `./src/index.js`:

```js
import React from 'react';
import { createStore, applyMiddleware, compose } from 'redux';
import { Provider } from 'react-redux';
import reducer from './reducer';
const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;
import createSagaMiddleware from 'redux-saga';

const store = createStore(
    reducer,
    composeEnhancers(applyMiddleware(sagaMiddleware))
);

sagaMiddleware.run(watchSagas);

ReactDOM.render(
    <Provider store={store}>
        <App />
    </Provider>,
    document.getElementById('root')
);

export default App;
```
