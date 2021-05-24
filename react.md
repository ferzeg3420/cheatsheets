
React is an open-source JavaScript library for building user
interfaces. It is used to create components, handle state and props,
utilize event listeners and certain life cycle methods to update
data as it changes.


React uses a syntax extension of JavaScript called JSX that allows you to write HTML directly within JavaScript. 

One important thing to remember: nested JSX must return a single element. So nest everything inside a single div

# The transpiler Babel is a popular tool transpiling JSX to javascript

```
const JSX = 
(
  <div>
    <h1> Hello </h1>
  </div>
);
ReactDOM.render(JSX, document.getElementById('root'));
```

# Render HTML to the DOM 

```
ReactDOM.render(MyComponentToRender, document.getElementById('SomeElementID'))
```

# Adding a class to JSX 

```
const JSX = (
  <div className="aCustomClass">
    <h1>The attribute name is className instead of just class</h1>
  </div>
);
```

# Break line, horizontal rule, self-closing tag syntax difference 

```
<br />
<div />
<hr />
```

# Stateless functional component 

```
const DemoComponent = function() {
  return (
    <div className='customClass' />
  );
};
```

# ES6 class syntax component 

```
class Kitten extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <h1>Hi</h1>
    );
  }
}
```

# Composing components 

```
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};
class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>I am the parent</h1>
        <ChildComponent /> # This is how you compose components
      </div>
    );
  }
};
```

# Render nested components 

# Pass Props (like arguments to components) to stateless functional components 

```
const Welcome = (props) => <h1>Hello, {props.user}!</h1>
```

# Pass an array as props 

```
<ParentComponent>
  <ChildComponent colors={["green", "blue", "red"]} />
</ParentComponent>
```

# Default props 

```
const FernandoLocator = (props) => {
  return (
    <div>
      <h1>Fernando</h1>
      <p>{props.location}</p>
    </div>
  )
};
Country.defaultProps = { location: 'San Francisco' }
```

# PropTypes to define prop types 

```
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};
Items.propTypes = { quantity: PropTypes.number.isRequired }
Items.defaultProps = {
  quantity: 0
};
```

# Using props in a ES6 class component 

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
            <p>{this.props.propName}</p>
        </div>
    );
  }
};
```

# Component State AKA stateful components 

```
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      someValue: ''
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

# Another way of rendering state (with a const in the render function 

```
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      someValue: ''
    }
  }
  render() {
    const name = this.state.name;
    return (
      <div>
        <h1>{name}</h1>
      </div>
    );
  }
};
```

# Set State with this.setState 

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    // Here's the function
    this.setState({
      name: 'Lewis'
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

# Bind this to a class method 

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    //The line below is how you do it:
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      name: 'Lewis'
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

# Set state to get the most current state 

Somehow the rocketship causes the function to get the most updated
state and props. Set state is asynchronous so it could have outdated
values.

```
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
// or 
this.setState(state => ({
  counter: state.counter + 1
}));
```

# For loop to create list items 

```
const textAreaStyles = {
  width: 235,
  margin: 5
};

class MyToDoList extends React.Component {
  constructor(props) {
    super(props);
    // Change code below this line
    this.state = {
      userInput: '',
      toDoList: []
    }
    // Change code above this line
    this.handleSubmit = this.handleSubmit.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  handleSubmit() {
    const itemsArray = this.state.userInput.split(',');
    this.setState({
      toDoList: itemsArray
    });
  }
  handleChange(e) {
    this.setState({
      userInput: e.target.value
    });
  }
  render() {
    const items = this.state.toDoList.map(x => <li>{x}</li>); // Change this line
    return (
      <div>
        <textarea
          onChange={this.handleChange}
          value={this.state.userInput}
          style={textAreaStyles}
          placeholder='Separate Items With Commas'
        />
        <br />
        <button onClick={this.handleSubmit}>Create List</button>
        <h1>My "To Do" List:</h1>
        <ul>{items}</ul>
      </div>
    );
  }
}
```

# Callbacks for sharing state back to parent component 

```
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputValue: ''
    }
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      inputValue: event.target.value
    });
  }
  render() {
    return (
       <div>
        { /* Change code below this line */ }
        <GetInput input={this.state. inputValue} handleChange={this.handleChange} />
        <RenderInput input={this.state.inputValue} />
        { /* Change code above this line */ }
       </div>
    );
  }
};

class GetInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Get Input:</h3>
        <input
          value={this.props.input}
          onChange={this.props.handleChange}/>
      </div>
    );
  }
};

class RenderInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Input Render:</h3>
        <p>{this.props.input}</p>
      </div>
    );
  }
};
```

# Hello World Example 

```
class HelloWorld extends React.Component {
  constructor(props)
  {
    super(props);
    this.state = {
    }
    this.handleChange = this.handleChange.bind(this);
  }

  handleChange(e) {
  }

  render() {
    return (
      <div>
        <p>Hello, World</p>
      </div>
    );
  }
}

React.render(<HelloWorld />, document.getElementById('app'))
```

# Lifecycle Method: Component Did Mount 

```
componentDidMount() {
  console.log("This method is called after a component is mounted to the DOM.")

}
```
