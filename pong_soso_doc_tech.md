# Introduction
As part of the 5100 module we have to create an online multiplayer game using the NekoEngine game engine, internal game engine at the SAE Institute Geneva school. This game must include at least one playable level and an interface for connecting at least two players.

# Pitch
The game PongSoso is a reproduction of the game Pong imagined by Nolan Bushnell and developed by Allan Alcorn in 1972. This game is inspired by table tennis in top view.

# Mechanics

## Paddle
Two players compete against each other by moving the racket vertically represented by a red or blue line to hit the ball.
There are limitations at the top and bottom of the screen so that the paddle cannot exit the screen from its ends.

![Limitation top and bottom for paddles](SosoLaMojo.github.io/assets/GIF/Pong_Soso_Limitation de hauteurPaddle.gif)

There are two inputs available (up and down), depending on the input chooses its change the speed of the paddle.
![Limitation and velocity player](SosoLaMojo.github.io/assets/Deplacement_et_limitation_player.PNG)

## Ball
There are limitations at the top and bottom of the screen so that the ball cannot exit the screen from its ends.

The speed of the ball increases each time the ball collides with a paddle board.
![Ball Velocity Increase](SosoLaMojo.github.io/assets/GIF/Pong_Soso_Velocity_balle_augmente.gif)

When there is a collision I refract the speed of the ball to make it bounce and I increase its speed by a constant.
![Ball Collision](SosoLaMojo.github.io/assets/Ball_collision.PNG)

The ball moves to the 0,0 position and returns to its base speed after leaving the field and take a life from the player.
![the ball returns to its base speed](SosoLaMojo.github.io/assets/GIF/Pong_Soso_balle_retourne_velocity_de_base.gif)

If the ball reaches a certain position in x (ballPoint) I move it to position 0,0 and reset its initial speed.
![The ball moves to position 0,0](SosoLaMojo.github.io/assets/Ball_respawn_position_zero.PNG)

## End of the game
**The goal** is for each player to take the **11 lives of the opponent**; lives that are lost when one player fails to return the ball to the other. A life score is displayed at the top of the screen.

![Player Win](SosoLaMojo.github.io/assets/GIF/Pong_Soso_Win.gif)

I check the lives of the players and when one of the players reaches 0, there is only 1 player left alive. The last player alive becomes the winner of the game.
![Check Winner](SosoLaMojo.github.io/assets/Check_Winner.PNG)
