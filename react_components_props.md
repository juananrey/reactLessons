React Components: props
------------------------

* Every component has an object named `props` , with certain information about the component.

* Any component can be initialized with certain `props` , which can be accessed later on via `this.props` calls:
```
<MyComponent foo="bar" />
...

class MyComponent extends React.Component {
    render() {
        const {foo} = this.props;
        return <h1>{foo}</h1>; // Renders `bar`
    }
}
```

* You can also pass values different from strings (between curly braces) and even arrays:
```
<Greeting name="Frarthur" town="Flundon" age={2} haunted={false} />
<Greeting myInfo={["top", "secret", "lol"]} />
```

* You can also pass props from one component to another: you simply need to pass the props from the parent Component to the rendered children (see example two lines above).

* We can receive event handlers as props!!! So that mean that any child can receive any function from the parent that could be executed there as part of the `this.props` scope.
```
class Talker extends React.Component {
  talk() {
    alert('taaaaalk');
  }
  
  render() {
    return <Button talked={this.talk} />;
  }
}

export class Button extends React.Component {
  render() {
    return (
      <button onClick={this.props.talked} >
        Click me!
      </button>
    );
  }
}
```

* Every `props` object has a property named `children` , which will contain anything in between the rendered component in case the component is not a self-closing tag (as in `<MyComponent />`):
```
<BigButton>
  I am a child of BigButton.
</BigButton>

console.log(this.props.children);  // Renders "I am a child of BigButton"
```

* You can load default properties in case the properties are not defined within the object, which should be an object, by using the `defaultProps` property, common to any React component:
```
class AddAddressComponent extends React.Component {}
...

AddAddressComponent.defaultProps = {
  cityList: [],
  provinceList: [],    
}
```
