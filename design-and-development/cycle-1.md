# 2.2.1 Cycle 1

## Design

### Objectives

My objectives for this phase are to create the JavaScript project and to create the basic layout for the environment in my game and to create a basic layout of where each of the buttons will be. This will allow me to begin working out functionality of these buttons.

* [x] Create the JavaScript project
* [x] Create a button which can be clicked to increase the value of "clicks" which is displayed to the user
* [x] Create a mutliplier system which makes the players clicks increase the score by a higher amount
* [ ] Create a cursor system which can be bought to automate clicks

### Usability Features

### Key Variables

| Variable Name   | Use                                                                             |
| --------------- | ------------------------------------------------------------------------------- |
| score           | Increases by one when the button is clicked and displays the value to the user. |
| multiplierCount | The number of multipliers the player has purchased.                             |
| cursorCost      | The cost to purchase multipliers.                                               |

### Pseudocode

```
score = 0
multiplierCost = 100
multiplierCount = 0

Display "Purchase Multiplier [100]" on the button

function incrementScore():
    Increase score by (multiplierCount + 1)
    Display "clicks: " + score

function purchaseMultiplier():
    if score >= multiplierCost:
        Decrease score by multiplierCost
        Increase multiplierCount by 1
        Multiply multiplierCost by 1.5
        Display "Purchase Multiplier [" + multiplierCost + "]" on the button
        Display "multipliers: " + multiplierCount
        Display "clicks: " + score

repeat every 1 second:
    if multiplierCount > 0:
        Increase score by (multiplierCount + 1)
    Display "clicks: " + score
```

## Development

```javascript
let score = 0;
let multiplierCost = 100;
let multiplierCount = 0;

document.getElementById("multiplierbutton").innerText = "Purchase Multiplier" + "[" + multiplierCost + "]"

function incrementScore() {
  score +=multiplierCount+1;
  document.getElementById("clicks").innerText = "clicks: " + score
}

function purchaseMultiplier() {
  if (score>=multiplierCost) {
    score -= multiplierCost;
    multiplierCount++;
    multiplierCost*=1.5
    document.getElementById("multiplierbutton").innerText = "Purchase Multiplier" + "[" + multiplierCost + "]"
    document.getElementById("multipliers").innerText = "multipliers: " + multiplierCount
    document.getElementById("clicks").innerText = "clicks: " + score
  }
}
```

This is the first javascript code I created. The first function increments the score by one (without any multipliers) and is called when a button is clicked. The second function is called when another button for purchasing multipliers is purchased.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gym Clicker Game</title>
</head>
<body>
  <button onclick="incrementScore()">Click</button>
  <p id="clicks"></p>
  <button id="multiplierbutton" onclick="purchaseMultiplier()">Purchase Multiplier</button>
  <p id="multipliers"></p>
</body>
<script src="main.js"></script></script>
</html>
```

This is the first HTML code I created. It adds two buttons which, when clicked call the functions mentioned in the JavaScript code which increase the value of score by 1 and the value of multiplierCount by 1. As multiplierCount increases, the rate at which score increases is raised.

```javascript
setInterval (function() {
  if(multiplierCount>0) {
    score +=multiplierCount+1;
  }
  document.getElementById("clicks").innerText = "clicks: " + score
}, 1000);
```

I then added this code which makes it so that the clicking process is automated once the first multiplier is purchased. If the value of multiplierCount is greater than 0, the value of score increases every 1000ms, or every second.

### Outcome

At the end of this cycle, I have created two buttons and a clicking system. When the button is clicked, the players score increases by one, this is the main feature of clicker games. This will allow me to create a shop system where players can use their score to purchase upgrades. I have also written a few functions, which do not yet work, but can be used when creating the shop and upgrades and boosts.

### Challenges

A challenge I faced was getting the display to update after being clicked. The value of clicks would increase but the web page did not show the number increasing.

## Testing

Evidence for testing

### Tests

| Test | Instructions  | What I expect     | What actually happens | Pass/Fail |
| ---- | ------------- | ----------------- | --------------------- | --------- |
| 1    | Run code      | Thing happens     | As expected           | Pass      |
| 2    | Press buttons | Something happens | As expected           | Pass      |

### Evidence
