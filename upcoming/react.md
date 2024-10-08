notes from doing the odin project intro to react.

I've used this as my means of getting my personal site up and running...

was all pretty straightforward getting set up using node and then get the boilerplate up and running with vite.

just used nvm for some reason was easier than using npm directly I believe.

today I am on to the first real step of components.

as part of this I came across html escape codes when you are looking to render certain characters in html.
these are used when you need to escape certain characters and they are called common html entities used for typography on wikipedia anyways.

Where do components live
So far our component is just hanging out in its own dedicated file.
This makes it independent from the rest of the codebase.
We can allow components to be integrated into the application using import and export.

for a very long time it was necessary to import React in your JavaScript files that used React components but since React v17 it is not longer required.

Let's export our newly created component so that parent components can use it as a child throughout your project.

export default FileName

what does this even mean? 
well I'm pretty sure that it just means that that is the default export from the module.
- You can only have one default export per module
- The default export cain be an y valid JavaScript value: a function, object, class or primitive

Ok so we've declared our component and export it but does main know about it yet?
No it does not

It's worth noting that one of the reasons it can't be a lower case reference to the component is that the jsx could be interpreted as a html element instead.

you can also do named exports as covered here
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export#description

what is a functional component?
It is just a component that is rendered by a javascript function.


javascript files are treated as modules if they have type of module in the script tag.

On the backend files with the mjs extension are modules.


what is jsx?
jsx is a syntax extension for JS that lets you write HTML like markup inside a js file.

essentially jsx is syntactic sugar for the React createElement function which takes like the html tag and some other arguments to create an object.
So the takeawy is that JSX compiles down to plain JS ojbects.

Typically we separate rendering logic and markup by havout them in separate files. JSx allows React to separatate concerns by containing both rendering logic and contetn int he same place i.e. a component.

On top of this its a more intuitive way to work with the UI inside your code.

Rules of JSX.
If you were to copy html into a react component it would not work.
This is due to some of the rules JSX implements, that aren't present in HTML.

- return a single root element.
If you want to return multiple elements in a compoennt you can do so by wrappign them in a parten tag.
That can be a div of if you don't want the elements to have a container you could use a React fragment which is just using empty angle brackets.

- close all tags.

Inhtml many tags are self closing but we must explicitly close them in jsx.

jsx turns into JavaScript and attributes of elements become keys of Javascript objects so you can't use dashes or reserved words such as class.

Referencing dynamic values in JSX.

just use curly braces and you're good to go.

from the react docs - JSX is a special way of writing Javascript.
That means it's possible to use Javascript inside it.

 Now that we have learned how JSX works and how to write it, this lesson will cover how we can render multiple elements and conditionally render UI in JSX.

The key attribute allows you to identify each element in a list.

starting to work with props
- will learn more about them in the near future
but for now they are arguments that are passed into componenets.
- need to set up each component to accept props as an arugment to the fuction
these are then passed as attributes to the component and can be accessed as such.
props as in properties.


Keys in React
Tn this lesson, we will cover keys in React. Keys are special props for our components and we'll learn why they are used.

Why does react need keys
In the previous lesson on rendering lists, we used the map method to iterate over an array of data and return a list of elements.
Now imagine, if any of the items in the list were to change, how would React know which item to update

you could rerender the entire list or
we hunt down the specific items that were changed and only re-render those.
Assuming we want to hunt down that one specific item that was changed then we need something to track it on.

We can track down a specific item by using a key.
React matches the keys of the previous list with the updated list.
And will only update the relevant one.

N.B. As long as keys remain consistent and uniqu, React can handle the DOM effectively and efficiently.

keys are passed in the component as a prop.

You can use the cryptop.randomUUID function to generate a unique id.

You could use the index of the element in an array however this is not recommended as this could change as items are deleted and added.
An important thing to remember though is that random keys should not be rendered on the fly as then they will just always be new and a new key will be generated on every render.
This will mean that enverying will just get re rendered.
In react data is transferred from parent components to child components via props.
This data transfer is unidirectional.
Any changes made to this data will only affect child components using the data andnot parent or sibling components.
this restriction on the flow of data gives us more explicit control over it, resulting in fewer errors in our application.


Ok so now that we know how data transfers between components then I suppose we need to say why this is useful.

Prop destructuring
A very commoon pattern you will come across in React is prop destructuring.
instead of the props keyword as the parameter of the component you can pass you can assign values to a destructured version of the ojbect

const obj = { a: 1, b: 2}
const {a,b} = obj
a will now equal 1
b will now equal 2.

we can also use default values for these deconstructed parameters in the event of them not being provided.

You can also make use of Button.defaultProps to set the values for this component.

Question: What is a Class Component?

Ok so the next thing will be looking into state so that is probably a good stopping point.

State is a component's memory

useState is a hook that allows you to define the state of a functional component.
It takes an initla value as a parameter and returns an array with two elements that we can destructure to get:
1. The current state value
2. A function to update the state value.

How does state work in React?
In React, when a component's state or props change, the component is destroyed and recreated from scratch.
The entire component is recreated but this time the latest state value will be returned from useState. This process is called rerendering.

whenever you set the value of state the associated component is rerendered.
The initial state value is only used for the components first render and subsequently ignored.

Hooks.
Hooks are functions that let you use React features.
All hooks are recognizable by the use prefix.

Hooks can only be called from the top level of a functional component.
Hooks can't be called from inside loops or conditionals.

Managing and structuring state effectively is by far one of the most crucial parts of building your application.
A general rule of thum is don't put values in state that can be calculated using existing values, state and/or props.

If you are using reference-type values, such as objects and arrays, never mutate them.

According to the React documentation we should trate state as if it was immutable. To change state, we should always use the setState function.
This is because if we don't provide a new object to setState it is not guaranteed to re-render the page.

setState use Object.is() to determine if the previou state is the same.

State updates are asycnhronous. What this implies is that whenever you call setState function, React will apply the update in the next component render.
Remember state varialbes aren't reactive, the component is N.B.

before the rerender is actually triggered the new value of state will not be reflected.
remember set state compares the objects and if they are different triggers a re render.

The actual updating of the value happens then when then component is rendered.
callbacks are functions which are passed as arguments and are evaluated at the end of the execution of a function.

prevState is available when you use the functional means of updating known as a functional update.
There are in fact many different implementations depending on the arguments passed for the useState hook.
N.B. When a callback is passed to the setState function, it ensures that the latest state is passed in as an argument to the callback.

If there are two calls to setState would this mean two rerenders?
No react is smart and wherever possible it batches the state updates.

Look into how react batches rerenders.
Multiple state updates within a single event handler or lifecycle method are batched together.
event handlers are javascript event handlers of course.
lifecycle methods are those from within react.

batching takes place within the current execution context which covers the above as well as all synchronous operations.

React 18 introduced automatic batching for all updates regardless of where they originate which expanded to current execution context to include more scenarios.

OK I'm on to the first project which is something to generate a CV so I should probably leave my learning there for today as I am tired...zzzz






















