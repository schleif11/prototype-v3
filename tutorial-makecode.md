### @activities true
# Collect the Banana Game Tutorial

## Example Game @fullscreen
In this tutorial, you'll code a simple game in which the player can collect an item. Here's an example of a completed game. 
![Collect the Banna's](https://raw.githubusercontent.com/schleif11/prototype-v3/master/images/1-fullgame.gif)

**Tutorial Objectives**
* Create a controllable player
* Create a collectable item
* Create a scoring system

By the end of this tutorial, you'll have the basic foundation of game in which you can add new features and mechanics to make your game even more fun!

## Create a controllable player 
### Step 1

Go to the "Scene" category and select the **set Background color to** block. Drag this block into the on start  block.


````blocks
scene.setBackgroundColor(9)
````

### Step 2
Select the "gray circle" in your **set Background color to** block and choose a color for your background.


### Step 3

Go to the "Sprites" category and select the **set mySprite to** block and drag this into the on start block.

````blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
`, SpriteKind.Player)
````

### Step 4

To draw your Player character, click the "gray square" in the **sprite of kind player**. You can select the "Gallery" button to choose a sprite or design your own in the editor. Click "Done" when you are finished.
![Add the Character](https://raw.githubusercontent.com/schleif11/prototype-v3/master/images/4-character.gif)

### Step 5

Go to the "Controller" category and add a **move (mySprite) with buttons** block **on start** block.

 
````blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . . . . f f f f f . . . . . . .
    . . . f e e e e e f . . . . . .
    . . f d d d d e e e f . . . . .
    . c d f d d f d e e f f . . . .
    . c d f d d f d e e d d f . . .
    c d e e d d d d e e b d c . . .
    c d d d d c d d e e b d c . . .
    c c c c c d d e e e f c . . . .
    . f d d d d e e e f f . . . . .
    . . f f f f f e e e e f . . . .
    . . . . f f e e e e e e f . f f
    . . . f e e f e e f e e f . e f
    . . f e e f e e f e e e f . e f
    . f b d f d b f b b f e f f e f
    . f d d f d d f d d b e f f f f
    . . f f f f f f f f f f f f f .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
````

## Create a collectable item
### Step 6

Now you should be able to control the Player character by using the "arrow" keys or "A,W,S,D" keys on your keyboard. Give it a shot!


### Step 7

Go to the "Sprites" category and drag another **set mySprite2** block into the **on start** block. This will be the item that the Player has to collect.

````blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . . . . f f f f f . . . . . . .
    . . . f e e e e e f . . . . . .
    . . f d d d d e e e f . . . . .
    . c d f d d f d e e f f . . . .
    . c d f d d f d e e d d f . . .
    c d e e d d d d e e b d c . . .
    c d d d d c d d e e b d c . . .
    c c c c c d d e e e f c . . . .
    . f d d d d e e e f f . . . . .
    . . f f f f f e e e e f . . . .
    . . . . f f e e e e e e f . f f
    . . . f e e f e e f e e f . e f
    . . f e e f e e f e e e f . e f
    . f b d f d b f b b f e f f e f
    . f d d f d d f d d b e f f f f
    . . f f f f f f f f f f f f f .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
MySprite2 = sprites.create(img`
`, SpriteKind.Player)
````

### Step 8

In the **set mySprite2 to** block, click on "mySprite2" to open the menu, and select "Rename variable." This variable can be named anything, but I'll rename mine to "banana" since my Player is a monkey and monkeys love to eat bananas! Once you have renamed your variable, click "Ok." 

### Step 9

In **set banana** to block, click on "Player" and select Food as the "sprite kind."

````blocks
scene.setBackgroundColor(9)
let mySprite = sprites.create(img`
    . . . . f f f f f . . . . . . .
    . . . f e e e e e f . . . . . .
    . . f d d d d e e e f . . . . .
    . c d f d d f d e e f f . . . .
    . c d f d d f d e e d d f . . .
    c d e e d d d d e e b d c . . .
    c d d d d c d d e e b d c . . .
    c c c c c d d e e e f c . . . .
    . f d d d d e e e f f . . . . .
    . . f f f f f e e e e f . . . .
    . . . . f f e e e e e e f . f f
    . . . f e e f e e f e e f . e f
    . . f e e f e e f e e e f . e f
    . f b d f d b f b b f e f f e f
    . f d d f d d f d d b e f f f f
    . . f f f f f f f f f f f f f .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
banana = sprites.create(img`
`, SpriteKind.Food)
````

### Step 10

Next, draw your Food sprite by clicking the gray square. Click "Done" once you have completed drawing your food.


### Step 11

Now we need to set up the code that will allow the Player to collect the food. Go to the "Sprites" category and drag the **on sprite overlaps otherSprite** block anywhere in the workspace.

````blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
})
````

### Step 12

In the **on sprite overlaps otherSprite** block, click on the second "Player" kind and change it to "Food."

````blocks
sprites.onOverlap(SpriteKind.Food, SpriteKind.Player, function (sprite, otherSprite) {
})
````

## Create a scoring system
### Step 13

Next, we need to add a point to the game score every time the player overlaps with the food sprite. Open the "Info" category and drag the **change score** block into the **on sprite overlaps otherSprite** block.

````blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
})
````

### Step 14
Now we need to randomize where the food pops up on the screen. Go to the "Sprites" category and drag a **set mySprite position to** block to the **on sprite overlaps otherSprite** block. Change the "mySprite" to your food.

````blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    
    info.changeScoreBy(1)
    banana.setPosition()
})
let banana: Sprite = null

````


### Step 15

Go to the "Math" category and drag a **pick random** block to the "X" coordinate in the **set food position** block. Do the same thing for the "Y" coordinate.

````blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    
    info.changeScoreBy(1)
    banana.setPosition(Math.randomRange(0, 0), Math.randomRange(0, 0))
})
let banana: Sprite = null
````

### Step 16

The arcade screen is 160 pixels wide and 120 pixels tall. We want the food to pop up within this area. In the first **pick random** block, change the maximum value from "10" to "160". In the second **pick random** block, change the maximum value to "10" to "120". Test your game to make sure it works properly.

````blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    
    info.changeScoreBy(1)
    banana.setPosition(Math.randomRange(10, 160), Math.randomRange(10, 120))
})
let banana: Sprite = null
````

## Challenge
### Step 17 @tutorialCompleted
Congratulations, you've coded your first game! Do you want to customize your game even more? Try adding a sound effect or an enemy that takes away points! Once you're done, click the "Finish" button. Then go back to the course page to learn how to save your project.

````blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.startCountdown(3)
    info.changeScoreBy(1)
    music.pewPew.play()
    banana.setPosition(Math.randomRange(10, 160), Math.randomRange(10, 120))
})
let banana: Sprite = null
````
