Virtual DOM
---

* In order to render JSX there are several techniques. The most common one is use `ReactDOM` to render it, as in this example. ReactDOM creates a Virtual DOM with a nodes hierarchy, which is finally rendered as HTML:
```
/* This code will load as virtual domain under an HTML element with id `app` */
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<h1>Hello world</h1>, document.getElementById('app'));
```

# Virtual DOM concept:

* In React, for every DOM object, there is a corresponding "virtual DOM object." A virtual DOM object is a representation of a DOM object, like a lightweight copy.
* In such representation, React just re-renders the page whenever it detects a diff between the current state and a previous snapshot, and _just involving the affected parts_ . Theoretically, this is what makes React so poweful.
* Here is the step-by-step:
    1) A JSX element renders.
    2) The entire virtual DOM updates.
    3) The virtual DOM "diffs," comparing its current self with its previous self.
    4) Part of the real DOM updates.
    5) The screen looks different than it used to.