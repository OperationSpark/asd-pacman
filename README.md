# asd-pacman
Building Pacman for the Advanced Software Development course using the ASD template

# To clone this template:

Enter these commands into your bash terminal to clone the repository and delete the `.git/` folder:

```bash
git clone https://github.com/operationspark/asd-pacman.git
rm -rf asd-pacman/.git
```

# Learning Objectives:
- Continue to recognize patterns and reuse functions from prior projects, adjusting them to work in a new context
- Generate a maze from a 2D array
- Manage HTML elements in a 2D array
- Bonus/Challenge: implement an A.I. algorithm for the ghost to chase Pacman

# Helpful jQuery methods:
```js
var $element = $("#id");                // references an existing element
var $element = $("<elementType>");      // creates a new element. don't forget the "<>"!

$element.appendTo($otherElement)        // inserts $element as a child of $otherElement
$element.detach()                       // removes the $element from its parent

$element.css("left", 100);              // sets the CSS "left" property value for $element to 100
$element.css("top", 50);                // sets the CSS "top" property value for $element to 50
$element.addClass("myClass");           // sets the class attribute value for $element to "myClass"
$element.attr("id", "abc")              // sets the id attribute value for $element to "abc"
$element.attr("src", "img/file.png");   // sets the src attribute value for $element to "img/file.png"
```

# The Maze

The data that represents the maze for Pacman is stored in the file `js/levels.js`. This file has a function, `getLevel(level)`, that accepts a String (such as "level1") which is used to return the 2D Array that represents various levels. While there is currently only one level, it would be easy to add more.

Your first task will be to create a helper function in `js/index.js` called `createMaze(level)` that first gets the 2D Array from `js/levels.js` and then, using nested `for` loops, generates the HTML elements for the level. Since the `js/levels.js` file is in the same folder as `js/index.js`, the `getLevel(level)` function may be called from anywhere inside `js/index.js`. Notice, however, that in the `index.html` the `level.js` file is loaded _before_ `index.js`. 

The 2D array will represent the level through a number system. `0` represents a square with a pellet inside, `1` represents a wall, and so on... Every single number in the 2D array requires that you create a `<div class='square'>` HTML element for that location and position that element in the correct coordinates based on its row and column position.

In addition, each `.square` element needs to have a unique `id` attribute assigned to it that follows the format: `r#c#` where the `#`s are replaced by the row and column position of that square in the 2D array. 

Use the HTML templates below to help you create the various kinds of square elements that exist in the maze:

```html
<!-- 9: empty square -->
<div class='square' id="r10c5"></div>

<!-- 0: pellet -->
<div class='square' id="r10c5">
  <div class='pellet'></div>
</div>

<!-- 1: wall -->
<div class='square wall' id="r10c5"></div>

<!-- 7: ghost gate -->
<div class='square gate' id="r10c5"></div>

<!-- 2: pacman -->
<img id='pacman' src="img/pacman"></div>

<!-- 3: red ghost -->
<img id='redGhost' src="img/redGhost.png"></div>

```

**NOTE**: Observe that **pacman** and the **red ghost** are not appended inside a `.square` element. Instead, they will be appended to the `$board` and move _above_ the maze.
