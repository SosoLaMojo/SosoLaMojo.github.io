# Game Design Document PongSoso

## INTRODUCTION

As part of the 5100 module we have to create an online multiplayer game using the NekoEngine game engine, internal game engine at the SAE Institute Geneva school. This game must include at least one playable level and an interface for connecting at least two players.

## GAMEPLAY

The game PongSoso is a reproduction of the game Pong imagined by Nolan Bushnell and developed by Allan Alcorn in 1972. This game is inspired by table tennis in top view.

Two players compete by moving the paddle vertically represented by a red or blue line to hit the ball. **The goal** is that each player reaches the score of **11 points before the opponent**; points that are earned when one player fails to return the ball to the other. A score is displayed for the current game. Walls are present at the top and bottom of the screen so that the ball cannot come out of the screen by its ends.

![LevelDesign](../assets/Pong_Soso.jpg)

## CONTROLS

![Input](../assets/InputPongSoso.png)

## BALL MECHANICS

When the ball is not returned by one of the players and comes out of the screen on the left or right the ball moves to position 0,0 with a velocity of 0. Then waits a few milliseconds before the server chooses the direction in which the ball takes off at certain velocity.
![Mecanic_Ball_1](../assets/Pong_Soso_Mecanic_Ball1.jpg)
![Mecanic_Ball_2](../assets/Pong_Soso_Mecanic_Ball2.jpg)
![Mecanic_Ball_3](../assets/Pong_Soso_Mecanic_Ball3.jpg)

#### BALL REBOUND

The player can change the direction of the ball based on the angle at which the ball hits the paddle using refraction.
![Mecanic_Ball_Rebond](../assets/Pong_Soso_Mecanic_Ball4.jpg)

## CHALLENGES

- Challenge 1: Ball mechanics
- Challenge 2: Ball rebound
- Challenge 3: Use of rollback for the 11 rounds of the game



##### [Return to home page](https://sosolamojo.github.io/)
