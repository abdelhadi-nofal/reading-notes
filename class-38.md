# React 


###  Conditional Rendering
 

 **In React, you can create distinct components that encapsulate behavior you need. Then, you can render only some of them, depending on the state of your application.** 


 Conditional rendering in React works the same way conditions work in JavaScript. Use JavaScript operators like if or the conditional operator to create elements representing the current state, and let React update the UI to match them.


##### Element Variables
 You can use variables to store elements. This can help you conditionally render a part of the component while the rest of the output doesn’t change.


Consider these two new components representing Logout and Login buttons:

`function LoginButton(props) {
  return (
    <button onClick={props.onClick}>
      Login
    </button>
  );
}

function LogoutButton(props) {
  return (
    <button onClick={props.onClick}>
      Logout
    </button>
  );
}

`

It will render either <LoginButton /> or <LogoutButton /> depending on its current state. It will also render a <Greeting /> from the previous example:



`class LoginControl extends React.Component {
  constructor(props) {
    super(props);
    this.handleLoginClick = this.handleLoginClick.bind(this);
    this.handleLogoutClick = this.handleLogoutClick.bind(this);
    this.state = {isLoggedIn: false};
  }

  handleLoginClick() {
    this.setState({isLoggedIn: true});
  }

  handleLogoutClick() {
    this.setState({isLoggedIn: false});
  }

  render() {
    const isLoggedIn = this.state.isLoggedIn;
    let button;
    if (isLoggedIn) {
      button = <LogoutButton onClick={this.handleLogoutClick} />;
    } else {
      button = <LoginButton onClick={this.handleLoginClick} />;
    }

    return (
      <div>
        <Greeting isLoggedIn={isLoggedIn} />
        {button}
      </div>
    );
  }
}

ReactDOM.render(
  <LoginControl />,
  document.getElementById('root')
);`

 
#####  Inline If with Logical && Operator 

You may embed expressions in JSX by wrapping them in curly braces. This includes the JavaScript logical && operator

It works because in JavaScript, true && expression always evaluates to expression, and false && expression always evaluates to false.


##### Inline If-Else with Conditional Operator

Another method for conditionally rendering elements inline is to use the JavaScript conditional operator condition ? true : false.

## Lists and Keys

Given the code below, we use the map() function to take an array of numbers and double their values. We assign the new array returned by map() to the variable doubled and log it:

`const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled);`


##### Rendering Multiple Components

You can build collections of elements and include them in JSX using curly braces {}.

##### Basic List Component

We can refactor the previous example into a component that accepts an array of numbers and outputs a list of elements.


