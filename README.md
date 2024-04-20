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
