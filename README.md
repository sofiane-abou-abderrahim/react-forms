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
