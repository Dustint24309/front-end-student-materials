# Events

Welcome back! Here's what we're working on in this lab:

## Learning Targets and Objective
- LT 1.12 - I can define a custom function and write code in the function body
- Objective: Animate a rocket by defining a `mouseClicked( )` function and writing code inside it

## Terminology Takedown
- **input**
- **events**
- **interact**
- **loading**
- **function**
- **function body**

## Before you start...

We'll do this before almost every lab. Use the `mkdir` command to create a new folder, and the `touch` command to create two new files.

`mkdir 02c-built-in-events`

`touch 02c-built-in-events/index.html`

`touch 02c-built-in-events/sketch.js`

Copy the code in the `index.html` file from our previous lab into our new `index.html` file.

## Intro

![rube goldberg](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/rube.gif)

When you interact with any program on your computer you are used to it being responsive to your input. 
Your input might be clicking certain things, moving your mouse to different areas, or pressing certain keys on the keyboard. 
These ways that you interact with the program are called **events**.

p5.js is actually *always waiting or listening* for certain events to happen. 
When the event does happen, it provides us, the programmer, a way to fire off code in response to the event.

We get to give the computer instructions like, "When the mouse is clicked do this", or "When the spacebar is pressed do this other thing". 
When the user does one of those things the code we provided will get run.

In a way, you have already seen the way events are handled in p5.  
What if we considered the web-page being loaded as an event. 
What happens with our p5 program when the page loads? 
What functions get called automatically?

If you said `setup` (called once) and `draw` (called repeatedly), you are totally correct! 
There's an event that occurs that says "Ok, the page is ready", when that happens p5 looks for those two functions with very specific names to be defined. 
Then it will run whatever code is inside those functions.

Other events will work the same way. 
When an event happens that says "Ok, the mouse was clicked", p5 will look for a specific function to be defined. 
If it is , whatever code inside the function will get run. If it's not, no big deal, nothing special will happen.


## `mousePressed( )` and `mouseReleased( )`

First things first, let's just make sure these functions work. 
We'll use `print` to confirm that a function named `mousePressed` is called when the mouse is pressed. 
To *define* a function we'll need to make it looks like the other functions we've defined such as `draw`.  
That means writing the word `function`, then the name of the function, then the open and close parenthesis `( )`,
and finally the open and close squiggly brackets, `{ }`. Everything that goes inside the squiggly brackets is called the function's body.


Start a new p5 project with only an empty canvas. Now add this:

```javascript
function mousePressed() {
  print('The mouse was pressed')
}
```

*Note: The quotation marks around `'The mouse was pressed'` are super important. Without them, the computer will think each one of these words is a variable name and your code will error because those variables don't exist.  Surrounding text with quotes, either single or double quotes are fine, makes the text what is called a String. Strings are another type of data, like numbers, that we will discuss much more later*

You should see something like this in the console every time you click.

![pressed](/resources/pressed.gif)

If you don't, check your spelling and syntax before moving forward.

Now that we've seen that function work, let's have it do something like change the color of a shape when the mouse is pressed.

With this code, you should be able to see something like in the gif below

```javascript
var col = 0

function setup() {
  createCanvas(400,400)
}

function draw() {
  fill(col)
  ellipse(mouseX, mouseY, 20, 20)
}

function mousePressed() {
  col = 255
}
```

![press event](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/press-event.gif)

Let's use the `mouseReleased` function to make this more like a real drawing app. When the mouse is pressed we'll draw, after it's released we'll get rid of the `stroke` and the `fill`.

```javascript
function setup() {
  createCanvas(400,400)
}

function draw() {
  noStroke()
  ellipse(mouseX, mouseY, 20, 20)
}

function mousePressed() {
  fill(0)
}

function mouseReleased() {
  noFill()
}
```

![cool](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/cool.gif)

#### 🔔🔑💡 Tip 💡🔑🔔
> In the first code snippet above I would have loved to call my variable `color` instead of the harder-to-understand `col`, Unfortunately `color` is a function in p5.  If I defined my own variable called `color` I would have **over-written** p5's function and could experience some weird behavior. Before declaring a new variable or a function it's always good to check that the name isn't already taken by p5.

## Mini-Challenges

### `mouseClicked()`
A mouse 'press' event means the mouse is being held down. A 'click', on the other hand, happens once exactly when the mouse is clicked.

- Your Mission, should you choose to accept it, is to use the `mouseClicked` function to launch a rocket.
Your goal is something like this:

![rocket launch](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/rocket-launch.gif)

Use this starter code:

```javascript
// some variables that determine how to draw the rocket
var groundLevel = 550
var rocketHeight = 80
var rocketWidth = 20
var rocketY = groundLevel - rocketHeight
var rocketX = 200 - rocketWidth/2

var rocketSpeed = 0

function setup() {
  createCanvas(400,600)
}

function draw() {
  background(250)
  // ground
  line(0, groundLevel, width, groundLevel)

  // rocket body
  rect(rocketX, rocketY, rocketWidth, rocketHeight)

  // rocket top
  triangle(rocketX, rocketY, rocketX + rocketWidth, rocketY, rocketX + rocketWidth/2, rocketY - 20)

  // increase the rocket's speed
  // rocketSpeed is initially set to 0
  rocketY += rocketSpeed
}

function mouseClicked() {
  // your code here...
}

```

**Hint:** *when the click event happens, what variable needs to change?*
