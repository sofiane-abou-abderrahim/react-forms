# Working with Forms & User Input

## It's Trickier Than It Might Seem

- What's Difficult About Forms?
- Handling Form Submission & Validating User Input
- Using Buil-in Form Features
- Building Custom Solutions

# Steps

## 0. Starting Project

1. run `npm install`
2. run `npm run dev`
3. create a `README.md` file

## 1. Handling Form Submission

1. in `login.jsx`, define a new `handleSubmit` function and bind it as a value to the `onSubmit` prop of the `<form>` element
2. add the `event.preventDefault()` function to prevent the default browser behaviour when submitting the form

## 2. Managing & Getting User Input via State & Generic Handlers

1. access to the value entered by the user with help of `useState()`
2. set up some change listener `handleInputChange` function & send it as a value of the `onChange` props
3. call the state updating functions inside of this `handleInputChange` function
4. feed the `event.target.value` back into the inputs by setting the `value` props equal to the state values
5. `console.log` the state values in the `handleSubmit` function

## 3. Getting User Input via Refs

1. copy the `Login.jsx` component & name it `StateLogin.jsx` to keep that code where we use state for tracking the user input
2. use refs instead of state
3. connect those refs to the input fields
4. use this connection inside of the `handleSubmit` function to get the entered email & the entered password

## 4. Getting Values via FormData & Native Browser APIs

1. add a `Signup.jsx` file to this project
2. output the `<Signup>` component in `App.jsx` instead of the `<Login>` component
3. in `Signup.jsx`, add a `handleSubmit` function & connect it to the `onSubmit` prop of the `form` element
4. inside of the `handleSubmit` function, use the `formData` constructor function built into the browser
5. as a result get back the form data object to get access to the data that was added to all the inputs in that form
6. for this to work, all those inputs must have the `name` prop
7. use the `get()` method to extract the value of a specific `name`
8. or even better, use the built-in `Object` class & call the `fromEntries` static method of that class
9. pass to it the result of the result of calling the `entries` method that form data object `fd`
10. calling `entries()` on the `fd` object will give you kind of an array of all the input fields and their values
11. and calling `Object.fromEntries()` on that array will give you an object where you have key value pairs for all your input fields
12. get back the lost multi value input fields & manually extract them & store them with the `getAll()` method
13. merge them into the `data` object by adding a new `acquisition` property to it
