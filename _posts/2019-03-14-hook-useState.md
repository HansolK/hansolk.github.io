<!-- ---
layout: post
title: React - basic syntax
---

I recently started to learn more about react and it is getting very interesting so I want to continue to talk about its basic syntax.

## Creating your first react component!
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
When you see the code above, you need to import React into your js file. The reason why we need to import React is, JSX is not valid javascipt. It is a syntax that helps us write React components. It converted to real javascript syntax through a tool like [babel](https://babeljs.io/). Once it is converted, it looks like this.
```javascript
render() {
      return React.createElement("div", null, React.createElement("h1", {
        className: "cool-component"
      }, "Welcome to My Blog"), React.createElement("p", null, "More contents are coming up!"));
    }
  }
```

```javascript
render() {
      return(
        <div>
          <h1>Hello world!</h1>
          <FavouriteMovies />
        </div>
      )
    }
```
I used render function to return the react elements. when you see `return` I used `()` because I am returning multiple elements like `<h1>` and another component called `<FavouriteMovies />`. Yeah, this is how you call another component. When you return multiple things, React want you to have a parent to wrap everything, I used  `<div>` here but you can put anything. There is `<React.Fragment></React.Fragment>`, a short syntax, `<>`,`</>`.  

# Wait. what is state?
Before we talk about state, just a heads up there are two ways to write React components - either as a function, or a class.
One of the major differences between functional and class components was *state*. Functional components are literally a function so you couldn't store any state, any state you wanted to have would have to be provided by its parent!
That parent would have to be a class component, at least, until a month ago.

Now, since the new React hooks have been released, you can now have state in functional components!

As I mentioned in my [first blog](2019-03-07-what-is-react.md), state provides a way for you to store information and have your component re-render when that information changes.
You might want to constantly update your counts each time you press button, but what if you have 10 different count buttons? How do you manage them all as they have different values? That's when state steps in. State is a shape of object so you can number of different states in each component. To use states, you need a constructor which is initialising state. You can also pass this state to different components using props! Props are also object.


## How do you change state?
It is very simple! I just changed the return part.
```javascript
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
I set onClick function on `<h1>`, so everytime when the `hello world!` clicks, I print the count number in the `<span>`. You have to use `{}` as it is javascript. 

That was the simple syntax, most of things are similart to Javascipt so once you get used to the some of the concepts, it will be easy to use! -->
