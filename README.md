🐍 Python Snake Game
This project implements the classic Snake game, showcasing fundamental Python programming concepts and the turtle graphics library through an object-oriented design. The game features real-time user input, collision detection, dynamic game state updates, and a persistent high-score system.

1. Project Goal
The primary goal was to develop a functional Snake game that demonstrates:

Modular Code Design: Organizing game components into distinct, manageable classes (Snake, Food, Scoreboard).

Interactive Graphics: Utilizing turtle for drawing and animating game elements.

Game Logic Implementation: Handling movement, growth, and various collision scenarios.

Data Persistence: Storing and retrieving the high score using file I/O.

3. How to Run
Prerequisites: Ensure Python 3.x is installed. The turtle module is part of Python's standard library.

Files: Place main.py, snake.py, food.py, and scoreboard.py in the same directory.

Execution: Run main.py

Controls: Use the Arrow Keys (Up, Down, Left, Right) to control the snake's direction.

5. Core Project Structure & Key Implementations
6. 
The project is structured into four main modules, each encapsulating a specific game entity or logic.

main.py - Game Orchestrator

Manages the main game loop, controlling speed (time.sleep(0.1)).

Registers keyboard events using screen.onkey().

Handles all collision detection logic:

Snake-Food: snake.head.distance(food) < 15.

Snake-Wall: Checking xcor() and ycor() against screen boundaries.

Snake-Self: Iterating through snake.segments[1:] and checking snake.head.distance(segment).

Triggers scoreboard.reset() and snake.reset() upon game over.

snake.py - Snake Mechanics

Movement Logic (move()): Implements a "segment-following" mechanism. Each segment (from tail to head-1) moves to the previous segment's position, then the head moves forward.

Direction Control: setheading() is used. Logic prevents immediate 180-degree turns (if self.head.heading() != DOWN:).

Growth (extend()): Adds a new segment at the last segment's position.

Reset (reset()): Clears all existing segments, moves them off-screen (as turtle objects are not garbage collected instantly), then re-creates the initial snake.

food.py - Food Generation

A simple turtle.Turtle subclass.

refresh() method uses random.randint() to place the food at random (x, y) coordinates within the game boundaries.

scoreboard.py - Score Management & Persistence

A turtle.Turtle subclass used for displaying text.

High Score Persistence: Reads (with open("data.txt") as data:) and writes (with open("data.txt", mode="w") as data:) the high score to data.txt. This ensures the highest score is saved across game sessions.

self.clear() is used before self.write() to update the score display without overlapping text.

4. Dependencies

All dependencies are standard Python library modules:

turtle: For all graphical output and event handling.

random: For random food placement.

time: To control game speed via time.sleep().
