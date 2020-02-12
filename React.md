## Native React 
#### Create a `new` react application with `create-react-app`
`yarn create react-app my-app`


## Typescript React 
#### Create a `new` typescript react project with `create-react-app` 
`yarn create react-app my-app --template typescript `
#### Convert Existing Native React to Typescript React 
```
yarn add typescript @types/node @types/react @types/react-dom @types/jest 
```
Next, rename any `.js` files to `.tsx` and restart development server





## React Libraries 
#### Material UI
`yarn add @material-ui/core@next ` //For NextJS  
`yarn add @material-ui/core`



## Useful Javascript and ES6 Features 
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