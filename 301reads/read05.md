
# Putting it all together

## How would you break a mock into a component heirarchy?
* draw boxes around every component .

* a component should ideally only do one thing If it ends up growing it should be decomposed into smaller subcomponent.

* We’ve italicized the data each component represents.

## What is the single responsibility principle and how does it apply to components?
* It is a computer-programming principle that states that every module, class or function in a computer program should have responsibility over a single part of that program's functionality.


## What does it mean to build a ‘static’ version of your application?
* a version that takes your data model and renders the UI but has no interactivity.

## Once you have a static application, what do you need to add?
* build components that reuse other components and pass data using props. 
* The components will only have render() methods. The component at the top of the hierarchy will take your data model as a prop. 
* If you make a change to your underlying data model and call ReactDOM.render() again, the UI will be updated. 

## What are the three questions you can ask to determine if something is state?
* Is it passed in from a parent via props? If so, it probably isn’t state.
* Does it remain unchanged over time? If so, it probably isn’t state.
* Can you compute it based on any other state or props in your component? If so, it isn’t state.


## How can you identify where state needs to live?

* Identify every component that renders something based on that state.
* Find a common owner component (a single component above all the components that need the state in the hierarchy).
* Either the common owner or another component higher up in the hierarchy should own the state.
* If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

## Things I want to know more about

### since React a one way data flow how chaild comunicate with others?
