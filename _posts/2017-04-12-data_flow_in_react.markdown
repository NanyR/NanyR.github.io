---
layout: post
title:  "Data flow in React"
date:   2017-04-12 01:34:53 +0000
---


In React data flows down from top level components to smaller components, it is passed through properties and state. A component doesn't know about its parent component that contains it, it only knows about itself and its children; having this unidirectional flow of data makes it so that, changes will flow down form main component updating each component as necessary. It is definitely challenging to wrap your head around the idea that we need to try and keep all of the state of our app in one place and think about how it will cascade down through our DOM tree to create the necessary functionalitites within our program, or how children components can have functionality if the state lives in another place outside of their component, normally in a parent component (which they don't even know about). At first I found it hard to think about triggering any events in child components, since essentially those events are meant to trigger other callback functions that will in turn trigger its parent's callback functions and so on until it reaches the main component, where state is, to indicate that a change needs to happen. This approach seemed tedious, and very strict. Especially when thinking about creating an app from scratch, the idea of passing down properties and managing state seemed overwhelming; do you start from biggest to smallest, or do start with the smallest components and build up from there?. Ultimately it is a matter of preference but according to the documentation, for simpler projects it is recommended to start with the highest component and work your way down to lowest components, and for more complex projects it is easier to work bottom up. I found this particular section of the documentation very useful [https://facebook.github.io/react/docs/thinking-in-react.html](http://), it basically goes through a step by step on how to approach a react application and think about components and state as a whole.
As I came to realize, with this unidirectional approach, tracking data within our app is easier since we know that it is coming from one place as opposed to having to look for something that might be coming from a bunch of different places. Another benefit of unidirectional data flow is that it works as a pure function, which operates on an input, and returns a value without altering or changing the input or causing any side effects in the program, and this gives you more control over the data and state of your entire application.
 



