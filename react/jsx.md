# JSX

JSX is an extension of the JavaScript language based on ES6 that handles rendering of React components that allow
 you to use `html` within `js` files. Internally all the html tags are replaced with calls to `React.createElement`, so
  this:

```jsx
const workshopTitle = <p>Devmeeting React + Redux</p>;
```

becomes this:

```jsx
const workshopTitle = React.createElement('p', {}, 'Devmeeting React + Redux');
```

This comes with couple of problems or gotchas, first of which is why you need to import React in every component file
 that uses jsx syntax, even when you don't reference it directly.

## Almost like HTML

Because the JSX code we write compiles into JavaScript, there are some reserved keywords that you can't use in your code.
Unfortunately, some of those keywords are quite useful in HTML code, like `class`. So in JSX we use `className` instead.

Here's a list of keywords we might run into and their replacements:

-   `class` becomes `className`,
-   `for` (used on labels to indicate which input they describe) should be replaced with `htmlFor`,
-   `tabindex` becomes `tabIndex` (capital 'I'),
-   `checked` works differently, for normal behavior use `defaultChecked`,
-   `onclick`, `onchange`, ... -> `onClick`, `onChange` all camel cased.

Other differences:

-   All attributes are case sensitive and have to be `camelCased`, no hyphens,
-   All elements can be self closing if they have no children (so `<div />` is legal),
-   `style` attribute takes and object of css-like properties (`{ backgroundColor: blue }`) [read more](https://reactjs.org/docs/dom-elements.html#style)
-   React elements have to always be wrapped in one single `HTML element`. If you don't want to use redundant element
 there is `React.Fragment` abbreviation `<>`

## Interpolation

Everything that goes between `{` and `}` will be evaluated as an JavaScript expression:

```jsx
const titleClass = 'workshop__title';
const workshop = {
    name: 'Devmeeting React + Redux'
};

<h2 className={titleClass}>{workshop.name}</h2>;
```

That also means that:

-   `if` _statement_ is not allowed, but a ternary _expression_ (`condition ? whenTrue : whenFalse`) is OK
-   `function` _statement_ cannot be used, but arrow function _expression_ can
-   `for` loops are _statements_, calling `.map` is an _expression_

## Iterating

```jsx
const fruits = ['banana', 'apple', 'orange']

 <div>{fruits.filter((element, index) => <span key={index}>{element}</span>)}</div>
```

### Resources

-   [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)
-   [JSX in Depth](https://reactjs.org/docs/jsx-in-depth.html)
