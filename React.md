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




# React Snippets 
#### React Class Component 
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
#### Hot Reload Module 
```
if(module.hot) {
    module.hot.accept();
  }
```




## Useful Javascript and ES6 Features 
#### Filter() : Take each item in list and apply a function to it and returns a list. Only items that the function returns true will be added to the return list.
### Ex. Returns a filtered list with only numbers < 10.
```
let myList = [1,2,3,4,5,10,20,30,40];

const updatedList = myList.filter((item) => item < 10);
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