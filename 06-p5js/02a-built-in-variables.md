# Built-in Variables

Welcome back! Here's what we're working on in this lab:

## Learning Targets and Objective
- LT 1.8 - I can describe how variables are containers that store data
- LT 1.9 - I can call functions using variables as arguments
- Objective: Design a drawing program with code to write your name in cursive

## Terminology Takedown
- **data**
- **variable**
- **value**
- **function**
- **argument**

## Before you start...

We'll do this before almost every lab. Use the `mkdir` command to create a new folder, and the `touch` command to create two new files.

`mkdir 02a-built-in-variables`
`touch 02a-built-in-variables/index.html`
`touch 02a-built-in-variables/sketch.js`

Copy the code in the `index.html` file from our previous lab into our new `index.html` file.

## Intro

By now you are familiar with a few of the functions provided by the p5 library. 
You've used **functions** like `ellipse( )`, `fill( )`, and `createCanvas( )`. Where did those come from?
You also have access to several built-in **variables**. 
A variable is a container that stores a **value**. 
"Value" means some actual data. So far the data we've seen has been different numbers. 
The numbers `0`, `100`, `255`, etc. are all different values.

## `width` and `height`

In our case we will be able to write the word `height` and it will be *as if* we were writing the number `600` or `200` or **whatever the height of the canvas is** from p5.js. 
Variables are dynamic, they can hold any different value.

Another way to think of a variable is like a bucket with a label on it. 
Inside of the bucket can be any value.  You use a variable by writing the name of the label on the outside of the bucket, 
but when you write the name you get the value that's inside the bucket.

To prove that these variables exist, we'll use the `print` function. If you open up the developer tools in Chrome and click in the console tab (by either right clicking the screen then clicking "Inspect" or use a keyboard, usually command+option+j) you will be able to see whatever is logged to the console with `print`.

![print width](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/print-width.gif)

As shown here, we see the *value* of the variable `width`, `800` logged to the console. In fact, it's logged many, many times in a row because `draw` is called repeatedly over and over. Each time it prints the value of the variable `width`. That's what the gray and white increasing number in the console indicates, the same output is being printed multiple times.

When we try to print a variable name that doesn't exist like `zebra`, we see a red JavaScript error that tells us `zebra` does not exist, it's not defined the way `width` and `height` are.

Here's how we could use these variables in our code:

```javascript
rect(width/2 - 25, height/2 - 25, 50, 50)
line(width/2, height/2, width/2, 0)
line(width/2, height/2, 0, height)
line(width/2, height/2, width, height)
```

## `mouseX` and `mouseY`
Two additional built-in variables `mouseX` and `mouseY` are also available to us. 
The value that they hold onto is the `x` or `y` coordinate of the mouse on the canvas. 
Try using `print` and see how the values change as you move your mouse.

```javascript
function draw() {
  background(225)
  print(mouseX)
  
  rect(width/2 - 25, height/2 - 25, 50, 50)

  stroke(200,200,200)
  strokeWeight(10)
  line(width/2, height/2, mouseX, mouseY)
}
```

Pretty cool!  `mouseX` and `mouseY` open up a lot of interesting possibilities.

## Mini-Challenges

1. Use `width` and `height` to divide the a canvas into 4 different color squares. The arguments you provide to draw each rectangle should only use a combination of `width`, `height`, and `0`.  Half the width would be `width/2` or `width * 0.5`

  ![4 squares](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/4squares.png)

2. Make a web using several `line`s.  The center of the web should move as you move your mouse.  There should be lines going from the center to all 4 corners as well as the midpoints of each side of the canvas.
 ![web](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/web.gif)

3. Use `mouseX`, `mouseY` and the `ellipse` function to make a program that can draw a line as you move your mouse. Write your name in cursive. If you have to dot an 'i' or cross a 't' (or an 'x')... good luck!


