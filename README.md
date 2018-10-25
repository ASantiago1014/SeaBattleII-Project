# Introduction to Sea Battle II
Sea Battle II is a Netbeans project that I finished in my CS 232 class. It is a simulation of the popular board game "Battleship", and has most of the same rules and mechanics. The game is played by guessing the placement of the opponenent's ships, and the first person to destroy their opponent's fleet is declared the winner. 

# How It Works
Sea Battle II utilizes an interactive GUI separated between a Model-View-Controller format to display two separate boards to each player whenever it reaches their turn: a board that displays the placement of their own fleet, and a tracking board that displays which squares on the opponent's board they have guessed. The placement of each player's fleet is randomized based on the bounds of the grid, each ship's length, and the placement of former ships. Every object in this program has their own image imported to the project, which is a series of .png files. The game also contains its own sounds for whenever a ship is hit or when a shot hits an empty square, shown by the .wav files. Between turns, the screen is changed to a black screen with a dialog box that indicates whenever it is the next player's turn, which requires the player to hit a button stating that they are ready. This is to prevent the previous player from seeing the current player's fleet locations. The game displays whether the player's shot is a hit or miss, and once a player destroys their opponent's fleet, the game will declare the player as the winner. 

# Classes

## AbstractController
This class is an abstract class that implements a PropertyChangeListener. It initializes two variables, both ArrayLists, for the different views and models for the program. This class contains methods to both add and remove views and models from their respective lists, inform all registered views of any change to update accordingly, and update the model whenever the view informs it of any user interaction. 

## AbstractModel
This abstract class contains methods to add and remove AbstractController subclasses as PropertyChangeListeners, and ensures those changes to the model are sent to the controller.

## AbstractView
This class is actually an interface that specifies an abstract method that receives a PropertyChange event from the controller and updates the view based on that event. 

## DefaultController
This class extends the AbstractController class, and has property names for each element and/or event associated with the models. This includes, for both players, when ships are deployed, when any squares or ships are hit, when any shots are a miss, or when the game is over. It also contains methods that are invoked by the Views based on any changes, preferably whenever a player's shot is fired.

## DefaultModel
This class initializes the two players from the Player class. It is here where the method to deploy the player fleets are located. In this method, for each ship, the location is totally randomized based on the bounds of the grid, the length of the ship in accordance to these bounds, and placements of other ships. One square is chosen, and adjacent squares are checked to see if they are empty. If the nuber of empty adjacent squares equal the ship's length, then the ship is placed. This class also contains methods for showing each player's fleet count, and setting the correct state for whenever a square is chosen: either a ship has been hit, or the shot has missed.

## EmptySquare
This is a simple class that extends the Square class. It contains one method for whenever the square is hit. The boolean flag in the Square class is set to true whenever an empty square is chosen. 

## Fleet
This class contains lists that specify the kinds of ships included in a fleet: one Carrier, one Battleship, two Destroyers, two Submarines, and three Patrol Boats. The class has the lists for the ship's sizes and names, and initializes an ArrayList of Ships. It also contains getter methods for the size and index of the ship.

## Grid
This class represents a grid of squares, which can be stated as a player's primary grid or n opponent's tracking grid. The constructor for the class fills the grid with empty squares based on the default size of the grid. It is in this class where the model calls the method to deploy the ships based on whether or not a row or column of squares is empty. It also contains a toString method that is mainly used for debugging and seeing how the game is being played, as well as getter and setter methods for Squares.

## Player
This class encapsulates the model for a player, and initializes a primary and tracking grid for that player. It contains getter methods for the grids and the count for their fleet, as well as methods for incrementing or decrementing the count. 

## Ship
This class initializes the basic information about a ship in the game. Each ship can be placed as either horizontal or vertical, and has variables accordingly. It also has variables for the ship's name, size, and alignment, as well as whether it has been sunk and how many hits it has accrued. The class contains methods for changing the state of the ship as a sunk ship, the x and y coordinates for the alignment, as well as getters for each instance field. Finally, it has a hit method that determines whether the ship has sunk based on the number of hits it has obtained. 

## ShipSquare
This class extends the square class and references the Ship object that is placed on a square. This class is also for helping to check which segment of the ship has been hit based on which ShipSquare has been hit. 

## Square
This abstract class represents a square placed on the primary grid. This class provides the boolean flag for the ship and empty square to determine whether or not the square has been hit. 

## ViewGridContainer
This class represents a container for a grid, and includes the grid and a JLabel for the grid's title. 

## ViewGridLabel
This class represents the view for a square in the grid. It contains a method for rotating the square for those which belong to ships that are deployed either vertically or horizontally. It also contains getter methods for the x and y coordinates for the grid label. 

## ViewMainWindow
This class implemets the AbstractView class and represents the main window for the game. This is the class that initializes the player cards, the sound files, and the image files for the game. It also contains each player's primary and tracking grids, containers, and grid labels. Finally, this class initializes the main window's components and invokes the model's property change event method based on which event is invoked.  

## ViewPrimaryGrid
This class implements the AbstractView class and represents the primary grid for each player. This class imports the images for the hit and miss icons, establishes the details for the primary grid, and initializes the components for it. This class also invokes the method to deploy the ships on the primary grid. 

## ViewTrackingGrid
This class is similar to the ViewPrimaryGrid class in that it represents the tracking grid for each player. It also imports the images for the hit and miss icons, as well as initializes the components for it. This class also utilizes methods for whenever a mouse cursor hovers over a square, which changes the color to orange. Finally, this class has a method for selecting squares.

# Conclusion
All of these classes come together to create one fun and relatively simple game for anyone. 
