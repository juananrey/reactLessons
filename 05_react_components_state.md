React Components: state
-----------------------

* Unlike `props`, a component's `state` is not passed in from the outside. A component decides its own state.

* Such state shall be given in the Component's constructor method:
```
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = { mood: 'decent' };
  }
}
```

* The `state` can be changed inside the component by calling `this.setState()` anywhere in the component:
```
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = { weather: 'sunny' };
    // This binding is necessary to make `this` work in the callback
    this.makeSomeFog = this.makeSomeFog.bind(this);
  }

  makeSomeFog() {
    this.setState({
      weather: 'foggy'
    });
  }
}
```

* `this.setState()` AUTOMATICALLY calls `render()` : As the status of the application is changed, the virtual DOM is changed and hence the app is re-rendered. This means that calling `this.setState()` inside `render()` method will cause an infinite loop!
