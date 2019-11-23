# Saga Concept

Saga is a pattern for handling events that can last undetermined amount of time and can cause calling other events. In Redux-Saga this pattern is implemented using JavaScript Generators. It helps handling side effects in application

## Generators

Generator is a function which return object with method `next`. By calling `next()` You can tell generator to go to the next stop moment represanted by `yield` keyword and return value. You can check this example in Your browser devtools

```js
function* iAmGeneratorFunction() {
    yield 'Hi';
    yield 1;
    yield { name: 'Apple', amount: 5 };
}

const iAmGeneratorObject = iAmGeneratorFunction();
console.log(iAmGeneratorObject.next());
console.log(iAmGeneratorObject.next());
console.log(iAmGeneratorObject.next());
```
