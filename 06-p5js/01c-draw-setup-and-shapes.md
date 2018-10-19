# Functions: `draw`, `setup`, and Shapes

Welcome back! Here's what we're working on in this lab:

## Learning Targets and Objective
- LT 1.3 - I can describe what a function is and how to create one using ( ) and { }
- LT 1.4 - I can explain the difference between calling a function and defining a function
- LT 1.5 - I know what an argument to a function is and can explain how they customize functions
- Objective: Draw the Olympic Rings using the ellipse function

## Terminology Takedown
- **function**
- **define**
- **call**
- **argument**
- **coordinates**
- **parameters**
- **documentation**


![dolphin](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/dolphin.gif)

Every artist needs a canvas. Obviously.

## Before you start...

We'll do this before almost every lab. Use the `mkdir` command to create a new folder, and the `touch` command to create two new files.

`mkdir 01c-draw-setup-and-shapes`

`touch 01c-draw-setup-and-shapes/index.html`

`touch 01c-draw-setup-and-shapes/sketch.js`

Copy the code in the `index.html` file from our previous lab into our new `index.html` file.

Paste this into your `sketch.js`:

```javascript
function setup() {
  createCanvas(640, 480)
}

function draw() {

  fill(225, 0, 150)
  noStroke()
  ellipse(mouseX, mouseY, 40, 40)
}
```

Preview your `index.html` and check out what happens when you move your mouse!

![we're drawing!](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/drawing.gif)

All the words you see above such as `createCanvas`, `fill`, or `ellipse` are
special words.  They need to be written exactly as shown above with exactly the same capitalization.

Don't take my word for it, replace the word `createCanvas` with `createcanvas` or
`fill` with a random word like `zebra`, what happens now when you preview your code.... nothing. If it ever happens
that you are writing some code and then you don't see what you expect or everything is broken
( \*\*SPOILER ALERT\*\* this will definitely happen, it's totally normal) check that you don't have any small typos
or spelling mistakes.

The technical term for these special words is **functions**.  

## What's a Function?

A function is a command or instruction written in code. When we want to give a command or tell our computer to do something we **call** a function. The syntax for calling a function is to write the name of the function followed by a set of parentheses like so `myFunction()`. Sometimes you may write more inside of the parentheses, we'll cover that really soon.

`ellipse`, for example, is a **function** another developer wrote that we can call on to tell the computer to draw an ellipse (circle).

You probably noticed the word `function` in the code above before `setup` and `draw`.  These are special **functions** that p5.js needs us to define.  They are special because p5 will call on them for us *automatically*.

Think back to flip-books you may have made as a child.

![flipbook](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/flipbook.gif)

#### `setup`

You can think of `setup` as a function that provides information like how big each page in your flip-book should be or how fast one should flip through. 
When a project has the p5.js library loaded into it, `setup` is *called one time when the page loads*

#### `draw`

`draw` also gets called automatically, though not just once. It gets called *repeatedly over and over again*.  
You can think of `draw` as saying what should go on each individual page of your flip-book.  
In our first code example, we tell `draw` to place an ellipse on the screen over and over again. 
It is the accumulation of all these ellipses one after the next that make it look like we are drawing a continuous pink line.

Inside of `setup` and `draw` is where we will write code and call on other functions to make things show up in the browser. 
"Inside" of a function means between the opening curly brace `{` and ending curly brace `}` you see after both functions.  
It may seem like a small thing, but if you don't put your code in the correct place inside of `setup` or `draw`, or accidentally delete a `}`, your code will work incorrectly.  

## Calling Functions & Arguments

As we said, calling a **function** is giving your computer a command to do something.  
Computer's follow the instructions you give them in the order you give them. 
Let's look more in depth at some of the instructions we've seen:

### `createCanvas`
Functions have names that describe what they do.
A function named `createCanvas` creates a canvas that we can draw shapes on.

It seems like creating a canvas is something that we would want to happen once at
the beginning of our project.  Given that information do you think we should call
the `createCanvas` function inside `setup` or inside `draw`?

If you guessed `setup` you are correct! Whatever code is inside `setup` will get run
one time when the page loads - just what we need.

In the code above there are some numbers after the name of the function:

```Javascript
createCanvas(640, 480)
```

What's going on there? Those numbers separated by commas are called **arguments** to
a function.

It's kind of like when we say `createCanvas` the computer is like,

```
"Alright, I will go ahead and make a new canvas for you, but I need a little more
info so I have a few questions."

"What should the width of the canvas be?"

"What should the height of the canvas be?"
```

The way we supply that information to our friendly computer is with arguments.

In between the parentheses we insert values for the width and height. So,
`createCanvas(250, 1000);` would create a skinny but tall canvas 250 pixels
across and 1000 pixels tall.


### `ellipse`

The `ellipse` function draws an ellipse shape on the canvas.  
We've seen the `ellipse` function called with 4 arguments:

```Javascript
ellipse(50, 50, 80, 80)
```

The *third* and *fourth* arguments determine the **width** and **height** of the ellipse.
If those values are the same you'll see a perfect circle, otherwise you'll have a squashed
circle that we call an oval. 

Play with those numbers and see how the circle changes.

So we know what some of the arguments to ellipse are:

`ellipse(?, ?, width, height)`.

If the *third* and *fourth* argument determine how big the ellipse will be, 
what do you think the *first* and *second* question marks should do to the ellipse?

---

## `x` and `y`

In math class, you've probably learned how to draw a point on a graph using `x` and `y` values.

That's exactly what the *first* and *second* arguments are for our ellipse function: `x` and `y` **coordinates** on the canvas.

### A Note on the p5.js Coordinate System

Usually, `x` and `y` coordinates have the **origin** `(0,0)` start in the **bottom left**.
The p5.js coordinate system is sort of different. `(0,0)` is actually the *top left* corner.

![coordinate plane](https://static1.squarespace.com/static/567458eda128e6372f9c1656/t/573cd44e4d088ee581102125/1463604324172/?format=2500w)

### The `rect` function

Ok, `rect` is a function we have never seen before. Nothing to fear here though, it works just like any other function. We call it and give it arguments.

```Javascript
rect(50, 50, 80, 80)
```

Try it, instead of a circle on the screen you'll see a square! `rect` works exactly like `ellipse` except it draws rectangular shapes!  
The arguments even specify the same information:

```Javascript
rect(x coordinate, y coordinate, width of rectangle, height of rectangle)
```

Play around with `rect`.  One thing to keep in mind is that the 1st and 2nd arguments, the `x` and `y` coordinates, determine where the *top left corner* of the rectangle will be placed.

## How Do You Remember All This?
### Reading Documentation
This seems like a ton of information.

Who can remember if the order of the arguments to `createCanvas`
is supposed to be `(width, height)` or was it `(height, width)`? 
Or let's say you want to draw a square. 
Ok great, you know what function to use...  wait-- was the function called  `rect` or `rectangle`?

Luckily p5 has amazing **documentation** that can be found [here](https://p5js.org/reference/).
Code documentation shows and describes how functions are intended to be used. Let's look at the documentation for the `line()` function. If you open the link above you'll find it under the heading "Shapes" in the section called "2D Primitives". Otherwise [this link](https://p5js.org/reference/#/p5/line) will take you directly there

### `line` Documentation In Detail
![Example](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/lineExample.gif)

#### Example
The Example section is a fully interactive window that allows you to change the arguments and see the results in real time. 
Try it!

#### Description
The next section provides an english description and any additional information. For `line` it reads:
>Draws a line (a direct path between two points) to the screen. 
The version of line() with four parameters draws the line in 2D. To color a line, use the stroke() function. 
A line cannot be filled, therefore the fill() function will not affect the color of a line. 
2D lines are drawn with a width of one pixel by default, but this can be changed with the strokeWeight() function.

#### Syntax and Parameters
![syntax and params](https://s3.amazonaws.com/upperline/curriculum-assets/p5js/syntaxandparams.png)

In the Example section of the documentation we saw the `line` function being passed number vales: `line(30, 20, 85, 75);`.

Where those numbers represent *actual data*, here in the Syntax and Parameters sections the documentation shows in a more general way how to use the function.  
We can see that *whatever* number we give as the first argument will be the `x` value for the first point and so on...

### Learning to Learn

Programmers look up documentation all the time. Basically, programming is challenging, and programmers want to spend their time and energy focusing on the challenging parts.  
So for things that are pure memorization like  the order of arguments and names of functions, you can let the documentation remember for you.

Referring to the documentation doesn't mean you are doing something wrong or aren't getting the hang of things. 
In fact, other developers would be impressed because it proves you are already learning how to independently teach yourself!

In a field where new technologies are always coming out and existing ones constantly change, that is an incredibly important skill.

## Mini-Challenge
1. Draw **5 shapes or lines** on the canvas using a minimum of **3 different functions**. Make it so that none of these 5 shapes touch each other and all fit entirely on the canvas

2. Change your code so each shape touches or overlaps at least one other shape.

3. Follow along with the documentation to do something you've never done before.
  - Some ideas:
  - Try a brand new function such as `quad` or `triangle`.
  - Look at the documentation of `rect` to see how to make a rectangle with rounded edges
  
4. Can you Build the Olympic Rings in Code?

![Olympic Rings](http://images.all-free-download.com/images/graphiclarge/olympic_rings_icon_clip_art_24458.jpg)


## Resources
- [p5.js Documentation](https://p5js.org/reference/)
