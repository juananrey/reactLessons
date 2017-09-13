# Stateless components update their parent's state.

```
class Parent extends React.Component {
  constructor(props) {
    super(props);

    this.state = { name: 'Frarthur' };
    this.changeName = this.changeName.bind(this);
  }
  
  changeName(newName) {
    this.setState({
      name: newName
    });
  }

  render() {
    return <Child name={this.state.name} onChange={this.changeName}/>
  }
}

```

* Such `Parent` component will allow any children to change the name of the user, by passing a function which changes such `state` to the children.

* There is something important to notice here: the `Parent` component is going to pass an [Event object](https://developer.mozilla.org/en-US/docs/Web/API/Event/target), as in the child this would be rendered as an event listener. This means, this won't work:

```
class Child extends React.Component {
  render() {
    return (
      <div>
        <h1>
          Hey my name is {this.props.name}!
        </h1>
        <select id="great-names" onChange={this.props.onChange}>
        ...
   )};
}
```


* The function to handle the event in the `Child` component should take an event object as an argument, extract the name that we want from that event object, and then call the event handler, passing in the extracted name. This will work:

```
class Child extends React.Component {
  constructor(props) {
    super(props);
    this.handleChange = this.handleChange.bind(this);
  }
  
  handleChange(e) {
    const name = e.target.value;
    this.props.onChange(name);
  }

  render() {
    return (
      <div>
        <h1>
          Hey my name is {this.props.name}!
        </h1>
        <select id="great-names" onChange={this.handleChange}>
        ...
   )};
}
```


