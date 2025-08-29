---
layout: default
title: Click the Circle
---

# 🎯 Worksheet 1: Click the Circle

**Your first Python game!** Today we're making a simple clicking game. In Scratch, you'd drag blocks. In Python, you'll type the code. Same ideas, new way of writing them!

## 📝 IMPORTANT: Type, Don't Copy!

**Type every line of code yourself** - don't copy and paste! Making mistakes and fixing them is how you learn. Your fingers need to learn where the symbols are!

**After each step:**
- Run your code to see what happens
- Change some numbers to see what they do
- Break it and fix it - that's how you learn!

---

## Part 1: Make a Window

Let's start super simple. Type this code exactly as shown:

```python
def setup():
    size(800, 600)

def draw():
    background(173, 216, 230)

run_sketch()
```

**Run it!** You should see a light blue window appear.

### What's happening?
- `setup()` runs once when your program starts (like "when green flag clicked")
- `draw()` runs over and over, 60 times per second (like a "forever" loop)
- `size(800, 600)` makes a window 800 pixels wide, 600 pixels tall
- The numbers in `background()` are RGB colors (Red, Green, Blue) from 0-255

### 🔬 Experiment Time!
Before moving on, try changing:
- The window size to `size(400, 400)` - what happens?
- The background numbers to `background(255, 0, 0)` - what color is that?
- What happens if you delete the `background()` line entirely?

Change it back when you're done experimenting!

<details markdown="1">
<summary>💡 Not working?</summary>

Check that:
- You have `def` before each function name
- The `:` colon is at the end of each `def` line
- The lines inside each function are indented (use Tab or 4 spaces)
- You spelled everything exactly right (Python is picky!)

</details>

---

## Part 2: Add a Circle

Now let's put a circle in our window. Add these lines to your `draw()` function:

```python
def draw():
    background(173, 216, 230)
    
    # Draw a red circle
    fill(255, 100, 100)
    circle(400, 300, 80)
```

**Run it!** You should see a light red circle in the middle of your window.

### What's new?
- `fill()` sets the color for shapes (like choosing sprite colors)
- `circle(x, y, size)` draws a circle at position x, y
- `#` makes a comment - Python ignores these, they're just for humans

### 🔬 Experiment Time!
- Change the circle position: try `circle(100, 100, 80)`
- Make it huge: `circle(400, 300, 300)`
- Try `fill(0, 255, 0)` - what color is that?
- What happens if you add another `circle()` line with different numbers?

---

## Part 3: Make It Clickable

Time to detect clicks! Add this new function at the bottom (before `run_sketch()`):

```python
def mouse_pressed():
    print("You clicked!")
```

**Run it and click anywhere!** Look at the console/output area - you should see "You clicked!" appear each time you click.

### 🔬 Experiment Time!
- Change the message to print your name
- Try printing `mouse_x` and `mouse_y` to see where you clicked
- What happens if you put `print("Hello")` in the `draw()` function instead?

<details markdown="1">
<summary>💡 Nothing happening when you click?</summary>

Make sure:
- The function is called exactly `mouse_pressed()` with underscore
- It's not indented (starts at the left margin like `setup()` and `draw()`)
- You're looking at the console/output window for the message

</details>

---

## Part 4: Add a Score

Let's count the clicks! Add a score variable at the very top of your program:

```python
score = 0

def setup():
    size(800, 600)

def draw():
    background(173, 216, 230)
    
    # Draw a red circle
    fill(255, 100, 100)
    circle(400, 300, 80)
    
    # Show the score
    fill(0)  # Black text
    text_size(32)
    text(f"Score: {score}", 20, 40)

def mouse_pressed():
    global score
    score = score + 1
    print(f"Score: {score}")

run_sketch()
```

**Run it!** Click anywhere and watch the score go up!

### Important: The `global` keyword
- When you want to change a variable inside a function, you need `global`
- This tells Python "I want to change the score variable from outside this function"
- In Scratch, variables just work everywhere - in Python, we need to be specific

### 🔬 Experiment Time!
- Try removing the word `global` - what error do you get?
- Change `score = score + 1` to `score = score + 10` for mega points!
- Add another text line showing "Click anywhere!" as instructions
- Change the text size and position

---

## Part 5: Only Count Circle Clicks

Right now clicking anywhere adds to the score. Let's fix that! We need to check if the click is inside the circle.

Update your `mouse_pressed()` function:

```python
def mouse_pressed():
    global score
    
    # How far is the mouse from the circle center?
    distance = dist(mouse_x, mouse_y, 400, 300)
    
    # Is it inside the circle? (circle radius is 40)
    if distance < 40:
        score = score + 1
        print("Hit!")
```

**Run it!** Now only clicking the circle increases the score!

### What's happening?
- `dist()` measures distance between two points (like sensing blocks in Scratch)
- `mouse_x` and `mouse_y` tell you where the mouse is
- `if` checks a condition - just like "if-then" blocks in Scratch
- The circle's radius is half its size (80 ÷ 2 = 40)

### 🔬 Experiment Time!
- Add an `else:` block to print "Missed!" when you click outside
- Try printing the exact distance value to see how it changes
- What happens if you change `< 40` to `< 100`? Why?

<details markdown="1">
<summary>💡 Score not going up?</summary>

The circle is at position (400, 300) with size 80, so radius is 40.
Make sure your `if` statement checks: `if distance < 40:`
Don't forget the `:` colon at the end of the if line!

</details>

---

## Part 6: Make the Circle Move

Let's make it a real game! First, add the random library and circle position variables at the top:

```python
import random

score = 0
circle_x = 400
circle_y = 300
```

Now update your code to use these variables:

```python
def draw():
    background(173, 216, 230)
    
    # Draw circle at its position
    fill(255, 100, 100)
    circle(circle_x, circle_y, 80)
    
    # Show the score
    fill(0)
    text_size(32)
    text(f"Score: {score}", 20, 40)

def mouse_pressed():
    global score, circle_x, circle_y
    
    # Check if clicked on circle
    distance = dist(mouse_x, mouse_y, circle_x, circle_y)
    
    if distance < 40:
        score = score + 1
        # Move circle to random position
        circle_x = random.randint(50, 750)
        circle_y = random.randint(50, 550)
```

**Run it!** Click the circle and it jumps to a new spot!

### What's new?
- `import random` lets us use random numbers (like pick random block)
- `random.randint(50, 750)` picks a random number between 50 and 750
- We keep the circle away from edges (50 pixels from each side)

### 🔬 Experiment Time!
- Change the random range to `random.randint(0, 800)` - what happens?
- Make the circle start at a random position (hint: call the random function in `setup()`)
- Try adding `print(f"Circle at: {circle_x}, {circle_y}")` to see where it goes

---

## 🎉 Complete Game!

You've made your first Python game! Here's the complete code:

```python
import random

score = 0
circle_x = 400
circle_y = 300

def setup():
    size(800, 600)

def draw():
    background(173, 216, 230)
    
    # Draw circle
    fill(255, 100, 100)
    circle(circle_x, circle_y, 80)
    
    # Show score
    fill(0)
    text_size(32)
    text(f"Score: {score}", 20, 40)
    
    # Instructions
    text_size(16)
    text("Click the circle!", 20, 70)

def mouse_pressed():
    global score, circle_x, circle_y
    
    distance = dist(mouse_x, mouse_y, circle_x, circle_y)
    
    if distance < 40:
        score = score + 1
        circle_x = random.randint(50, 750)
        circle_y = random.randint(50, 550)

run_sketch()
```

---

## 🚀 Make It Your Own!

Try these changes - type them yourself and see what happens!

### Easy Changes

**Color picker tip:** Use [rgbcolorpicker.com](https://rgbcolorpicker.com/) to pick any color! Copy the R, G, and B values (in that order) into your `fill()` or `background()` commands.

**1 - Change circle color** - Make your circle any color you want using RGB values

<details markdown="1">
<summary>💡 How to do it</summary>

Find the line `fill(255, 100, 100)` and change the three numbers.
- Try `fill(100, 255, 100)` for green
- Try `fill(100, 100, 255)` for blue
- Each number goes from 0 to 255

</details>

**2 - Change background color** - Give your game a different background

<details markdown="1">
<summary>💡 How to do it</summary>

Find `background(173, 216, 230)` and change the numbers.
- `background(0, 0, 0)` makes it black
- `background(255, 255, 255)` makes it white
- Mix your own RGB values!

</details>

**3 - Make it harder** - Shrink the circle so it's harder to click

<details markdown="1">
<summary>💡 How to do it</summary>

You need to change TWO things:
1. Find `circle(circle_x, circle_y, 80)` - change 80 to something smaller like 40
2. Find `if distance < 40:` - change 40 to half of your new circle size

If your circle is size 30, the distance check should be 15!

</details>

**4 - Change window size** - Make your game area bigger or smaller

<details markdown="1">
<summary>💡 How to do it</summary>

Find `size(800, 600)` at the beginning.
- First number = width, second = height
- Try `size(1000, 800)` for bigger
- Try `size(400, 400)` for a square window

Note: If you make it smaller, adjust the random numbers too (like `random.randint(50, 350)` for a 400px window)

</details>

**5 - Personalize the score** - Add your name to the score display

<details markdown="1">
<summary>💡 How to do it</summary>

Find `text(f"Score: {score}", 20, 40)`

Change the text inside the quotes:
- `text(f"Anna's Score: {score}", 20, 40)`
- `text(f"{score} points for you!", 20, 40)`
- Be creative!

</details>

### Challenges

<details markdown="1">
<summary>🎮 Challenge 1: Victory Message</summary>

Show "YOU WIN!" when the player reaches 10 points.

Hint: In your `draw()` function, add:
```python
if score >= 10:
    text_size(48)
    text("YOU WIN!", 300, 300)
```

</details>

<details markdown="1">
<summary>🎮 Challenge 2: Color-Changing Circle</summary>

Make the circle change to a random color each time it's clicked.

Steps:
1. Add three variables at the top for colors:
```python
circle_red = 255
circle_green = 100
circle_blue = 100
```

2. Use them in your fill: `fill(circle_red, circle_green, circle_blue)`

3. In `mouse_pressed()` when you hit the circle, randomize them:
```python
circle_red = random.randint(0, 255)
circle_green = random.randint(0, 255)
circle_blue = random.randint(0, 255)
```

</details>

<details markdown="1">
<summary>🎮 Challenge 3: Multiple Circles</summary>

Can you make TWO circles appear and keep track of which one you click?

This is tough! You'll need:
- Variables for `circle2_x` and `circle2_y`
- Another `circle()` command in draw
- Check distance to both circles in `mouse_pressed()`

</details>

<details markdown="1">
<summary>🎮 Challenge 4: Hover Points (No Clicking!)</summary>

Make the score go up just by hovering over the circle - no clicks needed!

Hint: Instead of checking in `mouse_pressed()`, check the distance in `draw()`:
```python
def draw():
    # ... your existing draw code ...
    
    global score
    distance = dist(mouse_x, mouse_y, circle_x, circle_y)
    if distance < 40:
        score = score + 1
        # Move circle immediately
```

Warning: This will make the score go up REALLY fast (60 times per second)!

</details>

---

## 🤔 Think About It

How is this similar to Scratch? How is it different?

- **Similar**: We have sprites (circles), sensing (mouse clicks), variables (score), and forever loops (draw function)
- **Different**: We type instead of drag, we need exact spelling, we use indentation to show what's inside what

