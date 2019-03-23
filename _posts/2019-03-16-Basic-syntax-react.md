---
layout: post
title: React - basic syntax
---

I recently started to learn more about react and it is getting very interesting so I want to continue to talk about its basic syntax.

Before we talk about anything else, just a heads up there are two ways to write React components - either as a function, or a class.
One of the major differences between functional and class components was *state*. Functional components are literally a function so you couldn't store any state, any state you wanted to have would have to be provided by its parent!
That parent would have to be a class component, at least, until a month ago.

Now, since the new React hooks have been released, you can now have state in functional components! I can talk about this in another post.


## Creating your first react class component!
```javascript
import React, {Component} from 'react';

class App extends Component {
  constructor(props) {
    super(props) 
    this.state = {
      count: 0
    }
  }
  render() {
    return(
      <div>
        <h1>Welcome to My Blog</h1>
        <p>More contents are coming up!</p>
      </div>
    )
  }
}
```
I will come back to state, so let's have a look at other syntax first.

Looking at the above code, the first important thing to note is that you need to import React into your js file.

The reason why we need to import React is, JSX is not valid javascipt. It is a syntax that helps us write React components. Once converted to real javascript syntax through a tool like [babel](https://babeljs.io/) it look something like this.
```javascript

render() {
      return React.createElement("div", null, React.createElement("h1", {
        className: "cool-component"
      }, "Welcome to My Blog"), React.createElement("p", null, "More contents are coming up!"));
    }
  }
```

When defining class components you will also need to import `Component` from React so you can correctly extend from their class component. However you aren't in the mood to import more things, you can also write it like this.

```javascript
class App extends React.Component 
```

When rendering out JSX, class components use a `render` function.
Inside this function you can see I wrapped the React elements in `()`, you don't have to use this, it is more of a styling choice. Some people choose to use this formatting instead

```jsx
render() {
  return <div>
      <h1>Welcome to My Blog</h1>
      <p>More contents are coming up!</p>
  </div>
}
```

## What about functional components?

```jsx
import React from 'react';

function FirstPost() {
  return(
    <div>
      <h1>This is My first post</h1>
      <p>what should you talk about?</p>
    </div>
  )
}
export default FirstPost
```

It looks very simliar to Class component's render method, and thats because it pretty much is!

## More than just html
The great thing about React is you can create your own components that render other components.
For example, earlier above we made an App component and a FirstPost component, lets pretend they are in the files 'App.js' and 'FirstPost'.

At the bottom of the FirstPost file, I have the code `export default FirstPost`, this is how you "export" a component so another one can use it. This isn't a React feature, but is just JavaScript.

Let's have a look at our App component again!
```jsx
import React, {Component} from 'react';
import FirstPost from './FirstPost';

class App extends Component {
  constructor(props) {
    super(props) 
    this.state = {
      count: 0
    }
  }
  render() {
    return(
      <div>
        <h1>Welcome to My Blog</h1>
        <p>More contents are coming up!</p>
        <FirstPost />
      </div>
    )
  }
}
```
Since we have exported the FirstPost component, we can import it into the App.js file. We then can then render the component out alongside out other html in the render method with the syntax `<FirstPost />`

As you notice both of my functional and class component wrap everything in a `<div>`. When you render multiple things, React wants you to have a single parent to wrap everything in, I used  `<div>` here but you can put anything. React also has a component called Fragment `<React.Fragment></React.Fragment>`, a short syntax, `<>`,`</>` which doesn't actually render anything to the page.

## Let's talk about state 
As I mentioned in my [first blog](2019-03-07-what-is-react.md), state provides a way for you to store information and have your component re-render when that information changes.
A simple example being keeping track of a count variable, that increments each time you press a button.
But what if you have 10 different count buttons? How do you manage them all as they have different values? That's when state steps in. State in class components is an object so you can have a number of different things in your state. To use state, you need a constructor whose job it is to initialise state. You then put the key and set the intial value!

## How do you change state?
It is very simple! I just changed the return part.
```jsx
return(
        <div>
          <h1 onClick={() => {
            this.setState({
              count: count + 1
            })
          }}>Hello world!</h1>
          <span>{this.state.count}</span>
          <FavouriteMovies />
        </div>
      )
```
In the example above, you can click `Hello world!`, you will be able to see the number of times you have clicked it. I am updating the count state by calling setState and setting the count as the previous state plus one.

These were some of the syntaxes you will encounter when you use React, most of things are similar to Javascipt, so once you get used to JSX syntax, React will be easy to use!
