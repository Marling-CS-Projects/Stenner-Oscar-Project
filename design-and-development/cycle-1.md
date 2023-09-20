# 2.2.1 Cycle 1

## Design

### Objectives

My objectives for this cycle are to create the JavaScript and HTML project and to create the basic layout and very simple user interface for my game and to create a basic layout of where each of the buttons will be. This will allow me to begin working out functionality of these buttons.

* [x] Create the JavaScript project
* [x] Create a button which can be clicked to increase the value of "clicks" which is displayed to the user
* [x] Create a cursor system which can be bought and to increase the rate at which score increases

### Usability Features

### Key Variables

| Variable Name | Use                                                                             |
| ------------- | ------------------------------------------------------------------------------- |
| score         | Increases by one when the button is clicked and displays the value to the user. |
| cursors       | The number of cursors the player has purchased.                                 |
| cursorCost    | The cost to purchase cursors.                                                   |

### Pseudocode

```
score = 1000
multiplierCost = 100
multiplierCount = 0
Set "Purchase Multiplier [100]" as the text of element with id "multiplierbutton"

function incrementScore():
    score = score + multiplierCount + 1
    Set "clicks: " + score as the text of element with id "clicks"

function purchaseMultiplier():
    if score >= multiplierCost:
        score = score - multiplierCost
        multiplierCount = multiplierCount + 1
        multiplierCost = multiplierCost * 1.5
        Set "Purchase Multiplier" + "[" + multiplierCost + "]" as the text of element with id "multiplierbutton"
        Set "multipliers: " + multiplierCount as the text of element with id "multipliers"
        Set "clicks: " + score as the text of element with id "clicks"
```

## Development

```javascript
let score = 1000;
let cursorCost = 100;
let cursors = 0;

let scoreInc = cursors

document.getElementById("multiplierbutton").innerText = "Purchase Cursor" + "[" + cursorCost + "]"

function incrementScore() {
  score+=cursors+1
  document.getElementById("clicks").innerText = "clicks: " + score
} //function which makes it so that the value of score increases every time the clicks button is clicked

function purchaseCursor() {
  if (score>=cursorCost) {
    score -= cursorCost;
    cursors++;
    cursorCost *=1.5;
    document.getElementById("multiplierbutton").innerText = "Purchase cursor" + "[" + cursorCost + "]"
    document.getElementById("multipliers").innerText = "cursors:: " + cursors
    document.getElementById("clicks").innerText = "clicks: " + score
  }
}
```

This is the first javascript code I created. The first function increments the score by one and is called when a button is clicked. The second function is called when another button for purchasing cursors is clicked. The more cursors the user has, the faster score increases.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gym Clicker Game</title>
</head>
<body>
  <h1>Gym Clicker Game</h1>
  <button onclick="incrementScore()">Click</button>
  <p id="clicks"></p>
  <button id="multiplierbutton" onclick="purchaseCursor()">Purchase cursor</button>
  <p id="multipliers"></p>
</body>
<script src="main.js"></script>
</html>
```

This is the first HTML code I created. It adds two buttons which, when clicked call the functions mentioned in the JavaScript code which increase the value of score by 1 and the value of cursors by 1. As cursors increases, the rate at which score increases is raised.

I created a very simple achievement system which I can improve as I continue to create my game. I did this by creating an array called achievements which stores whether each achievement is completed, by "true" for completed and "false" for not completed. Once the requirements are met, there is a list on the HTML code which will display the achievements. I also created a button which can be pressed to call this function and update the list of achievements.

### Outcome

At the end of this cycle, I have created two buttons and a clicking system. When the button is clicked, the players score increases by one, this is the main feature of clicker games. This will allow me to create a shop system where players can use their score to purchase upgrades. I have created a button which allows player to purchase cursors which increase the rate at which score increases.

I have also written a few functions, which do not yet work, but may be useful when creating the shop and upgrades and boosts in the future.

### Challenges

A challenge I faced was getting the display to update after being clicked. The value of clicks would increase but the web page did not show the number increasing.

As it the value is multiplied by a decimal, the value of multiplierCost becomes a very long decimal very quickly as the player purchases more multipliers. I will therefore have to make the value rounded as it increases.

## Testing

### Tests

| Test | Instructions          | What I expect                                                                                                              | What actually happens | Pass/Fail |
| ---- | --------------------- | -------------------------------------------------------------------------------------------------------------------------- | --------------------- | --------- |
| 1    | Run code              | Page opens with buttons for clicking to increase score and buttons to purchase cursors and buttons to update achievements. | As expected           | Pass      |
| 2    | Press click           | Score increases.                                                                                                           | As expected           | Pass      |
| 3    | Press purchase cursor | Cursor count increases and the rate and score increases at a faster rate.                                                  | As expected           | Pass      |

![](<../.gitbook/assets/image (1) (2).png>)

