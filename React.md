# Native React 
#### Create a `new` react application with `create-react-app`
`yarn create react-app my-app`


# Typescript React 
#### Create a `new` typescript react project with `create-react-app` 
`yarn create react-app my-app --template typescript `
#### Convert Existing Native React to Typescript React 
```
yarn add typescript @types/node @types/react @types/react-dom @types/jest 
```
Next, rename any `.js` files to `.tsx` and restart development server

# React Snippets and Libraries 
#### Material UI
`yarn add @material-ui/core@next ` //For NextJS  
`yarn add @material-ui/core`




# React Class Component  
### React Class Component 
```
import React from 'react';

class App extends Component {

    constructor(props) {
        super(props);
    }
    
    render() {
        ...
    }
}
```
### Pass props / Get Props / Children props 
```
<MyComponent
    prop_name1={value}
    prop_name2={value2}
>
    Child
</MyComponent>
```
### Get/Set State of a class component 
```
this.state
this.setState()
```
### Button Listener with params
```
<button
    onClick={ ()=> this.myHandler(params...)}
    type="button"
>
    Foo
</button>
```
### Hot Reload Module 
```
if(module.hot) {
    module.hot.accept();
  }
```

# React Functional Component 
### Declaration
```
//Pass in props 
function App(props) {
    const {value1,value2} = props;
    return ...
}

//Destruct props 
function App({value1,value2}) {
    return 
}

//Arrow Function with props 
const App = (props) => {
    const {value1,value2} = props;
    return ... 
}

//Arrow Function with destructing props 
const App = ({value1,value2}) => {
    return 
}

```
### React Hooks / Enable state for functional component 
#### useState() returns array with 2 item , 1st is the getter()  2nd is the setter() 
```
import React, { useState } from 'react';

const App = () => {
  const [greeting, setGreeting] = useState(<initialValue>);
  return <h1>{greeting}</h1>;
};

```


# Useful Javascript and ES6 Features 
#### Filter() : Take each item in list and apply a function to it and returns a list. Only items that the function returns true will be added to the return list.
#### Ex. Returns a filtered list with only numbers < 10.
```
let myList = [1,2,3,4,5,10,20,30,40];

const updatedList = myList.filter((item) => item < 10);
```
### Ex. Returns a filtered list with matching pattern
```
const isSearched = searchTerm => item => 
  item.title.toLowerCase().includes(searchTerm.toLowerCase());

this.state.myList.filter(isSearched(this.state.searchTerm));
```

#### Map() : Takes each item and apply function to that item
### Ex. Returns a list with all item * 2 
```
let myList = [1,2,3,4,5,10,20,30,40];
const updatedList = myList.map((item) => item * 2);
```

#### Classes 
```
class Developer {
    constructor(firstname, lastname) {
        this.firstname = firstname;
        this.lastname = lastname;
    }
}
const DIAO = new Developer('DIAO','SHEN');
```
#### Arrow Function don't need Block {} and return statement
```
list.map(item => {
    return (
        //statement1
        //statement2
    );
})

becomes 

list.map(item =>
    //statement 1
    //statement 2 
)

```
#### Destructuring Objects  
```
const user = {
    firstname: 'DIAO',
    lastname: 'SHEN',
};
```
```
const {
    firstname,
    lastname,
} = user;
console.log(firstname , lastname);
```
#### Destructuring Arrays
```
const users = ['DIAO' , 'SHEN'];
```
```
const [
    userOne,
    UserTwo,
] = users;
console.log(userOne , userTwo);
```
#### Create methods in object 
```
var myObject = {
    myMethod(params) {
        return ...
    }
}
```