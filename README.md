# React-Notes
Contains valuable code snippets of react.js framework which I consider really helpful to a beginner

JSX Outer Elements
There’s a rule that we haven’t mentioned: a JSX expression must have exactly one outermost element.

In other words, this code will work:

const paragraphs = (
  <div id="i-am-the-outermost-element">
    <p>I am a paragraph.</p>
    <p>I, too, am a paragraph.</p>
  </div>
);
But this code will not work:

const paragraphs = (
  <p>I am a paragraph.</p> 
  <p>I, too, am a paragraph.</p>
);
The first opening tag and the final closing tag of a JSX expression must belong to the same JSX element!

It’s easy to forget about this rule, and end up with errors that are tough to diagnose.

If you notice that a JSX expression has multiple outer elements, the solution is usually simple: wrap the JSX expression in a <div></div>.


*Rendering JSX*

You’ve learned how to write JSX elements! Now it’s time to learn how to render them.

To render a JSX expression means to make it appear onscreen.

Instructions
1.
The following code will render a JSX expression:

ReactDOM.render(<h1>Hello world</h1>, document.getElementById('app'));


*Rendering in Depth*
ReactDOM.render() I
Let’s examine the code that you just wrote. Start in previous.js, on line 5, all the way to the left.

You can see something called ReactDOM. What’s that?

ReactDOM is the name of a JavaScript library. This library contains several React-specific methods, all of which deal with the DOM in some way or another.

We’ll talk more later about how ReactDOM got into your file. For now, just understand that it’s yours to use.

Move slightly to the right, and you can see one of ReactDOM‘s methods: ReactDOM.render().

ReactDOM.render() is the most common way to render JSX. It takes a JSX expression, creates a corresponding tree of DOM nodes, and adds that tree to the DOM. That is the way to make a JSX expression appear onscreen.

Move to the right a little more, and you come to this expression:

<h1>Hello world</h1>
This is the first argument being passed to ReactDOM.render(). ReactDOM.render()‘s first argument should be a JSX expression, and it will be rendered to the screen.



ReactDOM.render() II
Move to the right a little more, and you will see this expression:

document.getElementById('app')
You just learned that ReactDOM.render() makes its first argument appear onscreen. But where on the screen should that first argument appear?

The first argument is appended to whatever element is selected by the second argument.

In the code editor, select index.html. See if you can find an element that would be selected by document.getElementById('app').

That element acted as a container for ReactDOM.render()‘s first argument! At the end of the previous exercise, this appeared on the screen:

<main id="app">
  <h1>Render me!</h1>
</main>

Passing a Variable to ReactDOM.render()
ReactDOM.render()‘s first argument should evaluate to a JSX expression, it doesn’t have to literally be a JSX expression.

The first argument could also be a variable, so long as that variable evaluates to a JSX expression.

In this example, we save a JSX expression as a variable named toDoList. We then pass toDoList as the first argument to ReactDOM.render():

const toDoList = (
  <ol>
    <li>Learn React</li>
    <li>Become a Developer</li>
  </ol>
);

ReactDOM.render(
  toDoList, 
  document.getElementById('app')
);

THE VIRTUAL DOM

The Virtual DOM

One special thing about ReactDOM.render() is that it only updates DOM elements that have changed.

That means that if you render the exact same thing twice in a row, the second render will do nothing:

const hello = <h1>Hello world</h1>;

// This will add "Hello world" to the screen:

ReactDOM.render(hello, document.getElementById('app'));

// This won't do anything at all:

ReactDOM.render(hello, document.getElementById('app'));
This is significant! Only updating the necessary DOM elements is a large part of what makes React so successful.

React accomplishes this thanks to something called the virtual DOM.



