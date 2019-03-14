---
layout: post
title: React - basic syntax
---

I recently started to learn more about react and it is getting very interesting so I want to continue to talk about its basic syntax.

## There are two ways of using components
### Functional components and Class components
The major difference between the functional component and class component was **state**. Functional component is literally function so you didn't need to store any states just wanted to return some html, however if you wanted to store state, your choice would've been class, at least, until a month ago. Now, since the new feature-hooks came out, the stories has changed. 

# Wait. what is state?
As I mentioned my first blog, state makes values easily manage. You might want to constantly update your counts each time you press button, but what if you have 10 different count buttons? How do you manage them all as they have different values? That's when state steps in. State is a shape of object so you can number of different states in each component. To use states, you need a constructor which is initialising state. You can also pass this state to different components using props! Props are also object.

```javascript
  class App extends Component {
    constructor(props) {
      super(props) 
      this.state = {
        count: 0
      }
    }
    render() {
      return(
        <React.Fragment>
          <h1>Hello world!</h1>
          <FavouriteMovies />
        </React.Fragment>
      )
    }
  }

```
When you look at my code, I used render function to return the html elements. when you see `return` I used `()`, this is because I am returning multiple elements like `<h1>` and another component called `<FavouriteMovies />`. When you return multiple things, React want you to have a parent, there is a component called fragment which is `<React.Fragment>`. There is a short syntax, `<>`,`</>`. It could be something like `</div>`, or anything else you want, React simply requires something to wrap everything.  

## How do you change state?
It is very simple! Let me use the same code above.
```javascript
return(
        <React.Fragment>
          <h1 onClick={() => {
            this.setState({
              count: count + 1
            })
          }}>Hello world!</h1>
          <span>{this.state.count}</span>
          <FavouriteMovies />
        </React.Fragment>
      )
```
I set onClick function on `<h1>`, so everytime when the `hello world!` clicks, I print the count number in the `<span>`. You have to use `{}` as it is javascript. 

That was the simple syntax, most of things are similart to Javascipt so once you get used to the some of the concepts, it will be easy to use!
