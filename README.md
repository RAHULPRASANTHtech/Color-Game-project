# Color-Game-project
# 🎨 Color Game using Python

## 📘 Project Overview
The **Color Game** is a fun Python-based graphical project that tests the player’s ability to recognize colors quickly.  
The game displays color names written in different font colors, and the player must correctly type the **color of the text**, not the word itself.  

This project helps demonstrate the use of **Tkinter (GUI)**, **event handling**, and **real-time user interaction** in Python.

---

## 🎯 Objectives
- To build an interactive color recognition game using Python.  
- To improve user concentration and reaction time through a fun activity.  
- To demonstrate the use of Tkinter GUI components and event-driven programming.  

---

## 🧠 Features
- 🕹️ Interactive GUI with dynamic text and colors.  
- ⏰ Countdown timer for limited gameplay time.  
- 💯 Real-time score tracking.  
- ⚙️ Randomized colors for each round.  
- 🔁 Option to restart the game after it ends.  

---

## 🛠️ Technologies Used
| Component | Description |
|------------|-------------|
| **Language** | Python 3.x |
| **Libraries** | `tkinter`, `random`, `time` |
| **Interface** | GUI-based window using Tkinter |



## 🗂️ Project Structure

---

## 🧩 How It Works
1. A color name is displayed on the screen in a random font color.  
2. The player must **type the color of the text**, not the word shown.  
3. Each correct answer increases the score.  
4. The game continues until the **timer runs out**.  

---

## 💻 Sample Code
```python
import tkinter as tk
import random

# List of possible colors
colors = ['Red', 'Blue', 'Green', 'Pink', 'Black', 'Yellow', 'Orange', 'Purple', 'White', 'Brown']
score = 0
time_left = 30

# Function to start the game
def start_game(event):
    if time_left == 30:
        countdown()
    next_color()

# Function to choose next color
def next_color():
    global score
    global time_left

    if time_left > 0:
        entry.focus_set()
        if entry.get().lower() == colors[1].lower():
            score += 1
        entry.delete(0, tk.END)
        random.shuffle(colors)
        label.config(fg=str(colors[1]), text=str(colors[0]))
        score_label.config(text="Score: " + str(score))

# Countdown timer
def countdown():
    global time_left
    if time_left > 0:
        time_left -= 1
        time_label.config(text="Time left: " + str(time_left))
        time_label.after(1000, countdown)

# Main GUI setup
root = tk.Tk()
root.title("🎨 Color Game")
root.geometry("400x300")

instructions = tk.Label(root, text="Type the color of the words, not the text!", font=('Helvetica', 12))
instructions.pack()

score_label = tk.Label(root, text="Press Enter to Start", font=('Helvetica', 12))
score_label.pack()

time_label = tk.Label(root, text="Time left: " + str(time_left), font=('Helvetica', 12))
time_label.pack()

label = tk.Label(root, font=('Helvetica', 60))
label.pack()

entry = tk.Entry(root)
root.bind('<Return>', start_game)
entry.pack()

root.mainloop()

