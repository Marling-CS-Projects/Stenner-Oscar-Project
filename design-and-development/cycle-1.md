# 2.2.1 Cycle 1

## Design

### Objectives

My objectives for this cycle are to create the JavaScript and HTML project and to create the basic layout and very simple user interface for my game and to create a basic layout of where each of the buttons will be. This will allow me to begin working out functionality of these buttons.

* [x] Create the JavaScript project
* [x] Create a button which can be clicked to increase the value of "clicks" which is displayed to the user
* [x] Create a mutliplier system which makes the players clicks increase the score by a higher amount
* [x] Create a cursor system which can be bought to automate clicks

### Usability Features

### Key Variables

| Variable Name   | Use                                                                             |
| --------------- | ------------------------------------------------------------------------------- |
| score           | Increases by one when the button is clicked and displays the value to the user. |
| multiplierCount | The number of multipliers the player has purchased.                             |
| multiplierCost  | The cost to purchase multipliers.                                               |

### Pseudocode

```
score = 1000
multiplierCost = 100
multiplierCount = 0

achievements = [false, false, false]

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

repeat every 1 second:
    if multiplierCount > 0:
        score = score + multiplierCount + 1
    Set "clicks: " + score as the text of element with id "clicks"

function checkAchievements():
    if score >= 10 and achievements[0] == false:
        achievements[0] = true
        Set "Reached score 10" as the text of element with id "achievement1"

    if score >= 100 and achievements[1] == false:
        achievements[1] = true
        Set "Reached score 100" as the text of element with id "achievement2"

    if multiplierCount >= 5 and achievements[2] == false:
        achievements[2] = true
        Set "Unlocked 5 multipliers" as the text of element with id "achievement3"
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

```javascript
function checkAchievements() {
  // Achievement 1: Reach a score of 10
  if (score >= 10 && achievements[0]==false) {
    achievements[0] = true;
    document.getElementById("achievement1").innerText = "Reached score 10";
  }

  // Achievement 2: Reach a score of 100
  if (score >= 100 && achievements[1]==false) {
    achievements[1] = true;
    document.getElementById("achievement2").innerText = "Reached score 100";
  }

  // Achievement 3: Purchase 5 multipliers
  if (multiplierCount >= 5 && achievements[2]==false) {
    achievements[2] = true;
    document.getElementById("achievement3").innerText = "Unlocked 5 multipliers";
  }
}
```

I created a very simple achievement system which I can improve as I continue to create my game. I did this by creating an array called achievements which stores whether each achievement is completed, by "true" for completed and "false" for not completed. Once the requirements are met, there is a list on the HTML code which will display the achievements. I also created a button which can be pressed to call this function and update the list of achievements.

### Outcome

At the end of this cycle, I have created two buttons and a clicking system. When the button is clicked, the players score increases by one, this is the main feature of clicker games. This will allow me to create a shop system where players can use their score to purchase upgrades. I have created a button which allows player to purchase multipliers which increase the rate at which score increases and also automates the clicking process for the player.

I have also written a few functions, which do not yet work, but may be useful when creating the shop and upgrades and boosts in the future.

### Challenges

A challenge I faced was getting the display to update after being clicked. The value of clicks would increase but the web page did not show the number increasing.

As it the value is multiplied by a decimal, the value of multiplierCost becomes a very long decimal very quickly as the player purchases more multipliers. I will therefore have to make the value rounded as it increases.

## Testing



### Tests

| Test | Instructions  | What I expect     | What actually happens | Pass/Fail |
| ---- | ------------- | ----------------- | --------------------- | --------- |
| 1    | Run code      | Thing happens     | As expected           | Pass      |
| 2    | Press buttons | Something happens | As expected           | Pass      |

### Evidence

![](<../.gitbook/assets/image (8).png>)

![](<../.gitbook/assets/image (2).png>)
