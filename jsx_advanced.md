JSX
---

* Javascript + HTML. It needs to be compiled. It loads in const anything that needs to be described.
```
const navBar = <nav>I am a nav bar</nav>;
```

* Also, such elements can hold attributes within them (as HTML does):
```
const title = <h1 id="big-header-foobar">Hellosh</h1>;
```

* A JSX expression _must_ have exactly one outermost element, Thus, it should be wrapped into a tag to work (return two different HTML elements won't work):
```
/* The valid element will work as it is within a div element. The other are considered as two different HTML elements and wont */
const valid = <div> <p>Hello</p> <p>World</p> </div>;
const invalid = <p>Hello</p> <p>World</p>;
```

* In order to render JSX there are several techniques. The most common one is use `ReactDOM` to render it, as in this example. ReactDOM creates a Virtual DOM with a nodes hierarchy, which is finally rendered as HTML:
```
/* This code will load as virtual domain under an HTML element with id `app` */
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<h1>Hello world</h1>, document.getElementById('app'));
```

* For JSX, you can't use the `class` attribute for the elements, as it is rendered into JS and is a reserved word in JS, so you use `className` instead.

* Also, you always need to use self-closing tags, as in `br` or `img` elements:
```
const valid = <div> <br/> <img src="#" /> </div>;
const invalid = <div> <br> <img src="#"> </div>;
```

* In order to render JS into the JSX, curly braces can be used `{}`:
```
const notRender = <h1> 2 + 3 </h1>    /* Renders 2 + 3 */
const render = <h1> {2 + 3} </h1>    /* Renders 5 */
```

* You can access variables declared as `const` within the whole JS file:
```
// Declare a variable:
const name = 'Gerdo';
// Access your variable from inside of a JSX expression:
const greeting = <p>Hello, {name}!</p>;
```

* The JSX elements can have `Event listeners`, as HTML elements do. You normally place the word `on`, followed by the name of the event you would like to listen to:
```
<img onClick={myFunc} />
```

*  You can't use `if` statements on JSX, but rather this sort of conditionals:
    -  Ternary operators as in `x ? y : z`.
    -  `&&` expressions: Just renders the JSX if the first sentence is true:
```
const tasty = (<ul>
    <li>Applesauce</li>
    { age > 15 && <li>Brussels Sprouts</li> }
    { age > 20 && <li>Oysters</li> }
    { age > 25 && <li>Grappa</li> }
  </ul>);
```

* Map avoids the `forEach` construct and renders elements in a pretty clear way:
```
const strings = ['Home', 'Shop', 'About Me'];
const listItems = strings.map(string => <li>{string}</li>);
<ul>{listItems}</ul>
```

* JSX lists are aware of unique attributes within the elements, called `keys`. Such attributes can also be part of the `.map` function if desired:
```
const people = ['Rowe', 'Prevost', 'Gare'];
const peopleList = people.map((person, i) =>
  <li key={'person_' + i}> {person} </li>
);
```
