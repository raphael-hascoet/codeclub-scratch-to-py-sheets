# Interactive Worksheet Syntax Guide

## For py5 Tutorial Creators

This guide shows all available interactive elements you can use in your worksheets. Everything here works with pure Markdown + HTML on GitHub and GitHub Pages - no setup required!

---

## 📚 Table of Contents

- [Basic Collapsible Sections](#basic-collapsible-sections)
- [Hints System](#hints-system)
- [Solutions & Answers](#solutions--answers)
- [Progressive Challenges](#progressive-challenges)
- [Interactive Checkpoints](#interactive-checkpoints)
- [Code Examples & Explanations](#code-examples--explanations)
- [Best Practices](#best-practices)

---

## Basic Collapsible Sections

### Simple Collapsible

<details>
<summary>Click to expand</summary>

This is hidden content that appears when clicked!

</details>

**Syntax:**

```html
<details>
  <summary>Click to expand</summary>

  This is hidden content that appears when clicked!
</details>
```

### With Emoji Icons

<details>
<summary>🎯 Learning Objectives</summary>

- Understand mouse events in py5
- Create interactive graphics
- Use variables to track state

</details>

**Syntax:**

```html
<details>
  <summary>🎯 Learning Objectives</summary>

  - Understand mouse events in py5 - Create interactive graphics - Use variables
  to track state
</details>
```

---

## Hints System

### Single Hint

<details>
<summary>💡 Need a hint?</summary>

Remember that `mouseX` and `mouseY` give you the current mouse position. You can use these anywhere in your code!

</details>

### Progressive Hints (Nested)

<details>
<summary>🤔 Stuck? Get hints here!</summary>

<details>
<summary>Hint 1: Where should the circle appear?</summary>

The circle should follow your mouse cursor. Think about which variables give you the mouse position...

<details>
<summary>Hint 2: Still stuck?</summary>

You'll need to use `mouseX` for the x-coordinate and `mouseY` for the y-coordinate of your circle.

<details>
<summary>Hint 3: Final hint!</summary>

Replace the fixed numbers in `circle(200, 200, 50)` with `circle(mouseX, mouseY, 50)`

</details>
</details>
</details>
</details>

**Syntax for nested hints:**

```html
<details>
  <summary>🤔 Stuck? Get hints here!</summary>

  <details>
    <summary>Hint 1: Where should the circle appear?</summary>

    The circle should follow your mouse cursor...

    <details>
      <summary>Hint 2: Still stuck?</summary>

      You'll need to use `mouseX` and `mouseY`...
    </details>
  </details>
</details>
```

---

## Solutions & Answers

### Basic Solution

<details markdown="1">
<summary>✅ Show Solution</summary>

```python
def setup():
    size(400, 400)

def draw():
    background(220)
    circle(mouseX, mouseY, 50)
```

</details>

### Solution with Explanation

<details markdown="1">
<summary>🎉 Complete Solution & Explanation</summary>

### The Code:

```python
def setup():
    size(400, 400)
    background(255)

def draw():
    # Don't clear the background - create a painting effect!
    fill(random(255), random(255), random(255))
    circle(mouseX, mouseY, 20)
```

### How it works:

1. **No background() in draw()** - This means previous circles stay on screen
2. **random(255)** - Generates random colors for each circle
3. **mouseX, mouseY** - Makes circles appear at cursor position

Try moving your mouse slowly for a snake-like effect!

</details>

---

## Progressive Challenges

### Multi-Level Challenge

#### 🎮 Challenge: Create a Click Counter Game

<details>
<summary>📝 Level 1: Basic Click Detection</summary>

Create a program that prints "Click!" to the console each time you click.

<details>
<summary>💡 Need help?</summary>

You'll need the `mousePressed()` function:

```python
def mousePressed():
    print("Click!")
```

</details>

<details>
<summary>✅ Solution</summary>

```python
def setup():
    size(400, 400)

def draw():
    background(200)

def mousePressed():
    print("Click!")
```

</details>
</details>

<details>
<summary>📝 Level 2: Count the Clicks</summary>

Now make it count how many times you've clicked and display the number on screen.

<details>
<summary>💡 Need help?</summary>

You'll need a global variable to store the count:

```python
click_count = 0  # Define outside functions

def mousePressed():
    global click_count
    click_count += 1
```

</details>

<details>
<summary>✅ Solution</summary>

```python
click_count = 0

def setup():
    size(400, 400)
    textSize(32)

def draw():
    background(200)
    text(f"Clicks: {click_count}", 150, 200)

def mousePressed():
    global click_count
    click_count += 1
```

</details>
</details>

<details>
<summary>📝 Level 3: Add a Target</summary>

Draw a circle target. Only count clicks when the user clicks inside the circle!

<details>
<summary>✅ Solution</summary>

```python
click_count = 0
target_x = 200
target_y = 200
target_size = 50

def setup():
    size(400, 400)
    textSize(32)

def draw():
    background(200)

    # Draw target
    fill(255, 0, 0)
    circle(target_x, target_y, target_size)

    # Draw score
    fill(0)
    text(f"Score: {click_count}", 150, 50)

def mousePressed():
    global click_count
    # Check if click is inside circle
    distance = dist(mouseX, mouseY, target_x, target_y)
    if distance < target_size/2:
        click_count += 1
```

</details>
</details>

---

## Interactive Checkpoints

### Self-Check Questions

#### ✓ Check Your Understanding

<details>
<summary>Question 1: What does `mouseX` represent?</summary>

**Answer:** `mouseX` represents the current horizontal (x) position of the mouse cursor within the sketch window, measured in pixels from the left edge.

</details>

<details>
<summary>Question 2: When does the `draw()` function run?</summary>

**Answer:** The `draw()` function runs continuously in a loop, approximately 60 times per second (60 FPS) by default, after `setup()` completes.

</details>

<details>
<summary>Question 3: How do you make something happen only when the mouse is clicked?</summary>

**Answer:** Use the `mousePressed()` function. This function is called once each time the mouse button is pressed down.

```python
def mousePressed():
    # Your code here runs once per click
    print("Clicked!")
```

</details>

---

## Code Examples & Explanations

### Expandable Code Walkthroughs

<details>
<summary>📖 Example: Color-Changing Background</summary>

### Complete Code:

```python
bg_color = 0

def setup():
    size(400, 400)

def draw():
    background(bg_color)

def mousePressed():
    global bg_color
    bg_color = random(255)
```

<details>
<summary>🔍 Line-by-line explanation</summary>

1. **`bg_color = 0`** - Creates a global variable to store our background color (starts as black)

2. **`def setup():`** - Runs once at the start

   - **`size(400, 400)`** - Creates a 400x400 pixel window

3. **`def draw():`** - Runs repeatedly (60 times/second)

   - **`background(bg_color)`** - Fills the background with our stored color

4. **`def mousePressed():`** - Runs once each time mouse is clicked
   - **`global bg_color`** - Tells Python we want to modify the global variable
   - **`bg_color = random(255)`** - Sets background to a random grayscale value

</details>
</details>

---

## Best Practices

### 📌 Tips for Using Collapsible Sections

<details>
<summary>View formatting tips</summary>

1. **Always leave a blank line** after `<summary>` tags when using markdown inside
2. **Use clear, action-oriented labels** like "Click for hint" or "Show solution"
3. **Use emoji sparingly but consistently**:

   - 💡 for hints
   - ✅ for solutions
   - 🎯 for objectives
   - 📝 for exercises
   - ⚠️ for warnings
   - 🎮 for challenges

4. **Structure hints progressively** - from vague to specific
5. **Include "Try it yourself first!"** messages before solutions

</details>

### 📝 Template for a Complete Exercise

<details>
<summary>View exercise template</summary>

````markdown
## Exercise: [Name]

**Goal:** [What students will create]

### Instructions

[Step-by-step what to do]

<details>
<summary>💡 Hints</summary>

<details>
<summary>Hint 1</summary>
[Gentle nudge]
</details>

<details>
<summary>Hint 2</summary>
[More specific help]
</details>

</details>

<details>
<summary>✅ Solution</summary>

```python
# Complete solution code
```
````

**How it works:**
[Explanation]

</details>

<details>
<summary>🚀 Bonus Challenge</summary>
[Extension activity for fast finishers]
</details>
```

</details>

---

## Testing Your Worksheets

### ✨ Quick Test Checklist

<details>
<summary>Before publishing, check these:</summary>

- [ ] All code blocks have proper syntax highlighting (```python)
- [ ] Hints progress from general to specific
- [ ] Solutions include explanations, not just code
- [ ] Tested on both GitHub and GitHub Pages
- [ ] Mobile-friendly (test on phone!)
- [ ] No nested details more than 3 levels deep
- [ ] All emoji render correctly
- [ ] Code is copy-pasteable

</details>

---

## Advanced Patterns

### Mix Content Types

<details>
<summary>🎨 Visual Reference: Color Values</summary>

| Color | RGB Code        | py5 Code          |
| ----- | --------------- | ----------------- |
| Red   | (255, 0, 0)     | `fill(255, 0, 0)` |
| Green | (0, 255, 0)     | `fill(0, 255, 0)` |
| Blue  | (0, 0, 255)     | `fill(0, 0, 255)` |
| White | (255, 255, 255) | `fill(255)`       |
| Black | (0, 0, 0)       | `fill(0)`         |

**Try it:**

```python
fill(255, 0, 0)  # Red
circle(200, 200, 100)
```

</details>

### Troubleshooting Sections

<details>
<summary>🔧 Common Errors & Fixes</summary>

<details>
<summary>Error: "NameError: name 'mouseX' is not defined"</summary>

**Cause:** You're trying to use `mouseX` outside of a py5 function.

**Fix:** Make sure you're using `mouseX` inside functions like `draw()` or `mousePressed()`, not at the top level of your code.

❌ **Wrong:**

```python
x = mouseX  # This won't work!

def draw():
    circle(x, 200, 50)
```

✅ **Correct:**

```python
def draw():
    x = mouseX  # Use it inside the function
    circle(x, 200, 50)
```

</details>

<details>
<summary>Error: "Nothing happens when I click"</summary>

**Cause:** Function name might be wrong.

**Fix:** Make sure it's `mousePressed()` not `mouse_pressed()` or `mousepressed()`

</details>

</details>

---

## 🎯 Remember

- This syntax works **everywhere** - GitHub, GitHub Pages, local preview
- No JavaScript or special setup needed
- Screen reader accessible
- Mobile friendly
- Can be copy-pasted by mentors

---

_Happy teaching! Feel free to copy any of these patterns for your worksheets._ 🚀
