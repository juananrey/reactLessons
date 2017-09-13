# Stateful and stateless components interacting

* It's quite usual that a component having its own state want to interact with a child component, so it can pass the state as a property to the child, which would be accessible via `this.props`:

```
import { Child } from './Child';
class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name : 'Frarthur'
    };
  }
  render() {
    return <Child name={this.state.name} />;
  }
}

...

export class Child extends React.Component{
  render() {
    return <h1>Hey, my name is {this.props.name}!</h1>;
  }
}
```

* We can also pass a function in the Parent component to be triggered by the child component by using the same technique (thus, rendering the child with the function itself as a `prop`).

* For the debate `props/state`, here is the clearest definition I could find:
    - _Props_ (short for properties) are a Component's configuration. They are received from above and immutable as far as the Component receiving them is concerned. A Component cannot change its props, but it is responsible for putting together the props of its child Components. Props do not have to just be data (callback functions may be passed in as props).

    - _State_ is a data structure that starts with a default value when a Component mounts. It may be mutated across time, mostly as a result of user events.A Component manages its own state internally. Besides setting an initial state, it has no business fiddling with the state of its children. You might conceptualize state as private to that component.