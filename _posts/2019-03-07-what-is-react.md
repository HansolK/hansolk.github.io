---
layout: post
title: What is React and why is it so popular?
---
This is my very first post, and I am going to talk about REACT!
If you are studying programming, you should have already or will come across this word! But what is it exactly? *Why* do people think it is so great?

## ...so what is it?

React is a JavaScript library for building user interfaces (frontend). 

Think of it this way, imagine you are becoming good friends with 'JS' but he is a bit of a lazy friend and requires you to do all of the work. Over time you are getting a bit tired of this, then one day you meet JS's new friend 'React'.
React is the older, wiser kid that knows a whole bunch of cool tricks to help make your life easier and has advice on how to deal with your other, lazier friend JS.
React being the great friend not only offers to help make your life easier, but can help you become better at interacting with JS!

What a great friend! 

This may be a strange analogy, but what I am trying to say is React will not only make building interfaces a whole lot easier, but it will also make you a better JavaScript developer as well!

I will show you some examples.


## A quick example
Lets say, I want to make a simple counter, where each time a button is pressed, the counter increases.

Click the 'increment' button!

<iframe src="https://codesandbox.io/embed/jj0vxjy5v5?fontsize=14" style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"></iframe>


This is an example that I created using just Javascript.
```javascript
  const wrapper = document.querySelector('.wrapper')
  const displayCount = document.createElement('span')
  const countButton = document.createElement('button')
  countButton.textContent = "increment"
  wrapper.appendChild(displayCount)
  wrapper.appendChild(countButton)

  let count = 0
  function increment(event) {
    count +=1
    displayCount.textContent = count 
  }

  countButton.addEventListener('click', increment)
```
As you can see, there is so much setup code, so many appendChilds, when all I want is a button that increases a count!
This doesn't even consider making the counter re-usable or cleaning up the counter once we are done with it.
![](https://media.giphy.com/media/nkLB4Gp8H6hFe/giphy.gif)
---

Let's have a look what I wrote using React.

```javascript
import React, { useState } from 'react';

function App () {
  const [count, setCount] = useState(0)
  return (
    <div>
      <span>{count}</span>
      <button onClick={() => {
        setCount(count +1)
      }}>increment</button>
    </div>
  )
}

```

Here I used React's fancy new way feature 'hooks' to manage my state.
This specific hook useState, returns an array where the first element is the current state and the second element is a function to update the state, causing the component to re-render. I will talk about the syntax and different ways of writing React in a future post. 

Without many lines of code, React helps you manage state quite easily. All you have to do is update the states, React will handle updating the html for you. This is why React is so irresistable!

