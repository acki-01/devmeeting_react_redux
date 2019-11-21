# What's in the project

We are going to be looking at the `src` directory:

## src/App.css

Styles for the `App` component.

## src/App.test.jsx

Unit tests for the component.

## src/App.jsx

Finally, the component file itself. There's some code written already that we'll replace.

-   capital "A" - all component names (and filenames) should be written in upper camel case, without any pre- or suffixes. ( :warning: according to AirBnB style-guide )
-   `export default App;` - default exports are a standard practice for React.
-   `return ( ...` - allows for better formatting

## src/index.jsx

Entry point of the whole operation, starts our React app with the `ReactDOM.render` line.
This is where most of the global stuff, like global styles, should go.

## src/index.css

Global styles

## src/logo.svg

Not interesting in itself, but why here and not in `/public` directory? `/public` contains only truly static assets,
while importing them into the component file allows for easier usage and webpack transformations.

## src/serviceWorker.ts

Contains the code for a default service worker enabling PWA style app.
Also, all files that don't contain components should be named using the lower camel-case style.

### Resources

-   [create react app docs](https://create-react-app.dev/docs/getting-started/)
-   [AirBnB Style Guide](https://github.com/airbnb/javascript/tree/master/react#naming)
