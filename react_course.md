REACT COURSE
------------

## Basics
- React has something called "state", which we can check in any page built in react.
- React operates with "Components", reusable pieces of code that can stay anywhere within your application.
- Furthermore, Componentes are actually Virtual DOM components (this is, copy/representation of the DOM object). If we change a component state, it would be reflected inmediately for **any** instance of such component, because react will call `render()` function each time that a `setState()` is invoked.

## 101 components
- Every class extends from `React.Component`, and should have **at least** one method, called `render()`.
- In order to render at least one element in your page, we can use `react-dom`: It's render method takes two parameters: a valid JSX (e.g. a react component with the notation: `<ComponentName/>`, and a mountpoint!
- React don't know anything about where the components are mounted, so in order to render a component you will need to do two things:
```js
// In the Component file, so the whole environment is aware that this component exists
export default ComponentName;

// In the main file that renders your application within a div
import ComponentName from './components/ComponentName';
render(<ComponentName/>, document.querySelector('#main'));
```

## HTML + JSX
- In react you **can't** return more than one element within the render page; you should make a parent-siblings relation instead.
- Or even better: wrap them into a `React.Fragment` tag! (Since React 16.2)
- For comments in JSX, you should use the JS interpret way `{ /* Comment */}`.

### React + CSS
- You can import it outside or inside the React realm. If you want to do that inside, simply call `import` within your Main React page.

## Passing dynamic data with .props
- Idea: passing data along components
- Props: those are like HTML parameters within a React `Component`.
- There are two types of values: strings (between `""`) and the rest (between `{}`). E.g: `<Header tagline="My tag" age={500} />`.
- We can use object destructuring to have all the information contained in props, as in: `const {tagline} = this.props;` (Further reference: https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/Destructuring_assignment#Object_destructuring).

## Stateless functional components
- Normal function VS arrow function (perks: implicit return if is a one liner, shorter syntax, **STATELESS**
```js
function Header(tagline) { // Normal function
    return ();
}
const Header = tagline => (); // Arrow function

const Header = ({tagline, age})  => (); // Arrow function with object destructuring in which we are passing `this.props` to this component!
```
- Stateless functional component: arrow function without any context knowledge (any `this.whatever`) which does the exact same functionality as a react component that a) has no context and b) has nothing but a `render()` method.

## React Router
```js
import { BrowserRouter, Route, Switch } from 'react-router-dom';
import StorePicker from './StorePicker';

const Router = () => (
    <BrowserRouter>
        <Switch> // This will try first the 1st route, if not the 2nd... if none matches, it will default to 404 not found!
            <Route exact path="/" component={StorePicker} />
            <Route path="/store/:storeId" component={App} />
            <Route component={NotFound} /> // This is the last fallback, so we don't include any path here
        </Switch>
    </BrowserRouter>
);
export default Router;

// On the index.js
import React from 'react';
import { render } from 'react-dom';
import Router from './components/Router';
render(<Router/>, document.querySelector('#main'));
```
