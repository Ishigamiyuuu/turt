import turtle
screen=turtle.Screen() # create a screen for turtle object and assign it to a variable named screen
tobject=turtle.Turtle() # instantiate a turtle object and assign it to a variable named tobject
tobject.color('blue')
tobject.pensize(8) # increase line thickness
tobject.speed(1) # lower tobject's drawing speed so that we can see the drawing process more clearly
xcoord=0 # create variables xcoord and ycoord to store coordinates for the .goto() commands that we will use later
ycoord=0

#  Draws the acute and the horizontal line (the first 2 strokes of the character from the top)
tobject.forward(75) # draws the horizontal line
tobject.penup() # prevent overlapping / drawing of new lines as we move tobject to a new position on the screen
tobject.goto(32.5,20) # move tobject to coordinates of the start position of the acute
tobject.right(45) # turn the tobject to face southeast
tobject.pendown()
tobject.forward(10) # draws the acute

# Draws the left curve below the horizontal line
tobject.penup()
tobject.goto(37.5,0) # move tobject to horizontal line's center (start point of left curve)
tobject.right(80) # turn tobject to face southwest
tobject.pendown()
for i in range (55):
    tobject.forward(1) # at each count of the loop, tobject will move 1 step forward and then rotate 0.25 degrees right. This will  occur 55 times and enables -
    tobject.right(0.25) # use to create the curve
    if i==27:
        xcoord, ycoord = tobject.position() # Assign the coordinates for a point along the left curve to xcoord and ycoord. This is starting point for the vertical line stroke

# Draws the vertical line and the 'hook' at it's end
tobject.goto(xcoord, ycoord) # move tobject to start point of vertical line (obtained by the if command in for loop above)
tobject.left(48) # turn tobject to face south
fwd1=38 # create a variable to represent the steps moved forward by tobject
tobject.pendown()
for i in range(2):
    if i == 1: # when i == 1, turn tobject to face northeast and set steps to be moved (fwd1) to be 15 steps
        tobject.left(135)
        fwd1 = 15
    tobject.forward(fwd1) # when i == 0, draw the vertical line. When i == 1, draw the hook
tobject.penup()

# Draw right curve and it's hook
tobject.goto(36,0) # Move to start point of right curve
tobject.right(120) # Turn to face southeast
tobject.pendown()
for i in range(67):         
    tobject.forward(1) # at each count of the loop, move tobject forward by 1 step and  rotate it 0.5 degrees left. This will create the curve effect.
    tobject.left(0.5)
    if i == 38:
        xcoord, ycoord = tobject.position() # Assign coordinates of a point along the right curve to xcoord and ycoord. This will be the start point for the 'hook'
tobject.penup()
tobject.goto(xcoord, ycoord) # go to start point for right curve's 'hook'
tobject.left(80) # turn to face northeast
tobject.pendown()
for i in range(18): # create a curved line to serve as the 'hook'
    tobject.forward(1)
    tobject.left(0.70)

screen.mainloop()
