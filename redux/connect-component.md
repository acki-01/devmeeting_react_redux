# Connect Component to Store

```jsx
import React from 'react';
import { connect } from 'react-redux';
import { addItem } from '../actions';

const SomeComponent = props => {
    return (
        <>
            <h1>SomeComponent, {props.otherData}</h1>
            <ul>
                {props.items.map(item => (
                    <div>
						<span>{item}</span>
						<button onClick={(() => props.onAddItem(item))}>
							Add
						</button>
					</div>
                ))}
            </ul>
        </>
    );
};

const mapStateToProps = state => ({
    items: state.storeName.items,
    otherData: state.storeName2.text
});

const mapDispatchToProps = dispatch => ({
    onAddItem: (item) =>
        dispatch(addItem(item)),
});

export default connect(
    mapStateToProps,
    mapDispatchToProps
)(SomeComponent);
```
