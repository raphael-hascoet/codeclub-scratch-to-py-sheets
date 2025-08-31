---
layout: default
title: Setup Guide - Thonny & py5
---

# 🔧 Setting up Thonny with py5 Mode

**For students and parents:** This guide will help you set up everything you need to start coding with Python and py5. Don't worry if you're new to this - we'll explain each step!

## 🤔 What are we installing?

<details markdown="1">
<summary>📝 What is Thonny?</summary>

**Thonny** is a simple code editor designed for beginners learning Python. Think of it like Google Docs or Microsoft Word, but for writing code instead of documents.

Why Thonny?

- Simple, clean interface - no confusing menus
- Built-in help for beginners
- Shows you exactly what your code is doing
- Free and works on all computers

</details>

<details markdown="1">
<summary>🎨 What is py5?</summary>

**py5** is a Python library that lets you create visual art, games, and animations. If you've used Scratch before, py5 gives you similar building blocks - but instead of dragging blocks, you type code!

With py5, you can:

- Draw shapes and colors
- Make interactive games
- Create animations
- Respond to mouse clicks and keyboard presses

The **py5mode plugin** makes it super easy to run py5 code in Thonny.

</details>

---

## 📋 What You'll Need

- A computer (Windows, Mac, or Linux)
- Internet connection (for downloading)
- About 10-15 minutes

---

## Step 1: Download and Install Thonny

### 📥 Download Thonny

1. Go to **[thonny.org](https://thonny.org)** in your web browser
2. Put your cursor on the download button for your computer to see the options, then click the first link:
   - **Windows**: Hover over Windows, click the first option
   - **Mac**: Hover over Mac, click the first option
   - **Linux**: Hover over Linux, run the commands they give

### 🔨 Install Thonny (Windows/Mac)

1. **Find the downloaded file** (usually in your Downloads folder)
2. **Double-click** the installer file
3. **Follow the installation steps**:
   - Click "Next" or "Continue" through the steps
   - Accept the default settings (don't change anything)
   - Wait for it to finish installing

---

## Step 2: Install the py5mode Plugin

### 🚀 Launch Thonny

1. **Find Thonny** on your computer:
   - **Windows**: Look in the Start Menu
   - **Mac**: Look in Applications folder or Launchpad
2. **Double-click** to open Thonny
3. If it asks about settings, choose **"Standard"** (the default)

### 🔌 Install the Plugin

1. In Thonny, click **Tools** in the top menu
2. Choose **"Manage plug-ins..."**
3. In the search box, type exactly: `thonny-py5mode`
4. Click the **blue "thonny-py5mode"** link when it appears
5. Click the **"Install"** button
6. Wait for it to download and install
7. **Close Thonny completely** and **reopen it**

<details markdown="1">
<summary>💡 Can't find the plugin?</summary>

Make sure you:

- Spelled it exactly: `thonny-py5mode` (with hyphens)
- Are connected to the internet
- Wait a moment for search results to appear

If it still doesn't work:

- Try closing and reopening the plug-in manager
- Make sure you're using the latest version of Thonny

</details>

---

## Step 3: Activate py5 Mode

### 🎯 Enable py5 Mode

After restarting Thonny, you should see a new **"py5"** menu at the top.

1. Click the **"py5"** menu
2. Choose **"Imported mode for py5"**
3. If prompted about downloading Java (JDK), click **"Yes"** or **"Allow"**
4. Wait for the download to complete (this only happens once!)

<details markdown="1">
<summary>❓ Don't see the py5 menu?</summary>

The py5 menu should appear after installing the plugin and restarting Thonny.

If you don't see it:

1. Make sure you completely closed and reopened Thonny
2. Check that the plugin installed correctly (Tools > Manage plug-ins)
3. Try restarting your computer

</details>

<details markdown="1">
<summary>☕ What's this Java download about?</summary>

**py5** needs Java to run (don't worry, you won't need to learn Java!). Think of Java like the engine that powers py5's graphics.

- This is a one-time download
- It's completely safe and automatic
- It might take a few minutes depending on your internet speed

</details>

---

## Step 4: Test Your Setup

### 🧪 Run a Test Program

Let's make sure everything works! Type this code into Thonny:

```python
def setup():
    size(400, 300)
    background(200, 220, 255)

def draw():
    fill(255, 100, 100)
    circle(mouse_x, mouse_y, 30)

run_sketch()
```

### ▶️ Run It!

1. Click the **green "Run"** button (or press F5)
2. **You should see**: A light blue window with a red circle that follows your mouse!

<details markdown="1">
<summary>✅ Success! What just happened?</summary>

Congratulations! Your setup is working perfectly. Here's what the test code does:

- **`setup()`**: Creates a 400x300 pixel window with a light blue background
- **`draw()`**: Runs 60 times per second, drawing a red circle wherever your mouse is
- **`mouse_x` and `mouse_y`**: Tell the program where your mouse is located
- **`run_sketch()`**: Starts the program running

Move your mouse around in the window and watch the circle follow it!

</details>

<details markdown="1">
<summary>❌ Nothing happened?</summary>

**No window appeared:**

- Make sure you clicked the "Run" button (green triangle)
- Check that py5 mode is activated (py5 menu should show a checkmark)
- Try restarting Thonny

**Error messages:**

- Make sure you typed the code exactly as shown
- Check that all the colons (:) are in the right places
- Make sure the lines are indented properly (use Tab or 4 spaces)

**"py5 is not defined" error:**

- py5 mode isn't activated - go back to Step 3

</details>

---

## 🎉 You're Ready to Code!

**Congratulations!** You've successfully set up Thonny with py5 mode. You're now ready to start creating games and animations with Python!

### 🚀 What's Next?

<details markdown="1">
<summary>📚 Ready for your first project?</summary>

Now that your setup is complete, you can start with our interactive worksheets:

**[Click the Circle - Your First Game!](worksheets/sheet-1-click-the-circle)**

This worksheet will teach you:

- How to create a game window
- Drawing shapes and colors
- Detecting mouse clicks
- Keeping score

Don't worry about understanding everything at first - just type the code and see what happens!

</details>

---

## 🆘 Still Need Help?

<details markdown="1">
<summary>📞 Getting More Help</summary>

**If you're still having trouble:**

1. **Ask your Code Club mentor** - they're there to help with exactly these kinds of setup issues!
2. **Ask for help**: Show this guide to a parent, teacher, or tech-savvy friend
3. **Double-check each step**: Go through this guide again slowly

**Remember:** Setting up programming tools can be tricky the first time, but once it's working, you'll be able to create amazing things!

</details>

---

_🎯 Ready to start coding? Head to [your first worksheet](worksheets/sheet-1-click-the-circle)!_
