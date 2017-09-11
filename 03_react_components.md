React Components
----------------

* `React.Component` is a JavaScript class. To create your own component class, you must extend it:
```
import React from 'react';
class MyComponentClass extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
}
```

* We can use conditionals after declaring the `render()` function and before the `return` statement, as JSX doesn't like classic `if/else` logic.

* The keyword `this` is widespread along some examples on React. Technically, it can be used within the `render()` method and it points out to the object which is enclosing the method, in this case, an `IceCreamGuy` instance. Thus, the example below will work as `food()` is a getter method and thus do not need the parentheses.
```
class IceCreamGuy extends React.Component {
  get food() {
    return 'ice cream';
  }

  render() {
    return <h1>I like {this.food}.</h1>;
  }
}
```

* Please note that if the outter method (e.g. food) would need to be aware of something about the class, _we would need to bind also the context there_, as in:
```
<button onClick={this.addCountryToBlockedList.bind(this)}> Add </button>
```

* React components can as well render another components; plus, you can render them and pass them properties or arguments to the constructor:
```
class OMG extends React.Component {
  render() {return <h1>Whooaa!</h1>;}
}

class Crazy extends React.Component {
  render() {return <OMG {...this.props} property1={someProperty}/>;}
}
```




