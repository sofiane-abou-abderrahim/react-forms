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

## 5. Resetting Forms

1. if you are managing the input with state, reset those state values (see `StateLogin.jsx`)
2. if you're getting the entered values with refs, reset the inputs by manually setting the value property of the connected input elements to empty strings as in `Login.jsx` (but not really recommended)
3. instead if you're working with refs, it's typically better to reset the form with help of the `reset()` function as in `Signup.jsx` (imperative code again, but less code)
4. comment out the code snippets responsible for resetting the forms

## 6. Validating Input on Every Keystroke via State

1. in `App.jsx`, render the `<Login>` component imported from `./components/StateLogin.jsx` to get the stateful version of that login form
2. validate the `email` input on every keystroke by adding a computed value named `emailIsInvalid` to this `StateLogin.jsx` component
3. set this `emailIsInvalid` constant based on the email state value which you're managing, so here we could say that `emailIsInvalid` should be true if the entered email does not include an `@` symbol
4. update the UI by outputting an error message if this `emailIsInvalid` is true
5. make sure that `emailIsInvalid` is only set to true if the user did start entering a value

## 7. Validating Input Upon Lost Focus (Blur)

1. in `StateLogin.jsx`, react to the email input field losing focus by adding the `onBlur` event listening Prop to it
2. add a new `handleInputBlur` event handling function
3. manage a new `didEdit` state, because now, we don't just wanna keep track of the value that has been entered into an input, but we also wanna keep track of whether the user touched this value or not
4. update this state in the `handleInputBlur` function
5. trigger this `handleInputBlur` function as a value to the `onBlur` prop
6. use this new `didEdit` state to perform validation
   1. And we can check whether `emailIsInvalid` by not checking for whether it still has the initial value `enteredValues.email !== ''`
   2. but by instead keeping this check `!enteredValues.email.includes('@')` and combining this check with `didEdit.email`
7. remove this error message as soon as the user starts typing again so that he has another chance of entering a valid value until he's done typing and the input loses focus again at which point of time this validation should run again
   1. in `handleInputChange`, also update`didEdit` on every keystroke
   2. reset the `email` & `password` properties to `false` whenever the user starts typing again

## 8. Validating Input Upon Form Submission

1. switch back from the `StateLogin.jsx` version of the `Login` form to the ref-based `Login` form in `App.jsx`
2. since we wanna stick to refs, you can basically only validate the input when the user submits the form
   1. in the `handleSubmit` function, determine whether the email is valid, by adding the `emailIsalid` constant
   2. when the form is submitted, perform your check by checking if you don't have an `@` symbol in that email with the `includes`
3. reflect this error in your form with some `emailIsInvalid` state
4. you can also add submission-based validation in `StateLogin.jsx` even if you are already validating the user input on every keystroke because it is always a good idea

## 9. Validating Input via Built-in Validation Props

1. switch back to `Signup.jsx` in `App.jsx`
2. add the browser built-in `required` prop to validate the inputs & form control elements
3. add the browser built-in `minLength` prop to the `password` input
