# Parallax Juicy Button

Challenge done in 1 week (I wasn't available the first week)
https://www.swisstransfer.com/d/f69dc331-dc84-4f97-84ea-a14326981ea2

## Controls

Move - WASD / Arrows
Look - Mouse
Interact - LMB (Press or Hold)

Goal - Score the highest number & try to have the same 3 digits

## Main features

- 1 player (Animations + Interaction)
- 1 button
- 1 Changing number widget
- 1 Score counter widget
- 3 VFX (Confetti / Money rain / Button press)
- 4 SFX + 1 BGM (FMOD Integration)

The goal was to make the juiciest button possible but before pressing any button I focused on a simple character with a button pressing animation. Everything around button is important, every signals you give the player help to make something "juicy" 
After that the button, so it was the main focus (VFX, SFX, Animation).
I started to focus on everything around it, a basic gameplay but with big numbers to make it satisfying.
Finaly, added some visuals and a BGM to make the player stay.

More informations on what I was plannig to add in the "Why you chose this structure" part.

## How the project is structured

### Player
- The player uses the a Input Map Control + Input Asset
- Left click plays a custom animation 
- Player Model is base arm from UE5 
- Took the original Animation blueprint. Deleted everthing useless and added logic over it
- Made a custom pressing button animation via AI (Quickmagic AI)

- Animation montage with notifies for the code + montage section to spam the animation (Hold LMB)
- Sphere Trace to detect if any thing can be interacted (via an interface to avoid casting)


### Button

- Interactible interface inmplementation with an onPressed event
- when pressed play SFX + VFX + animation
- Simple Animation via Timeline (Scale Based)
- SFX have a random pitch + a higher pitch each time its pressed

![image](https://github.com/user-attachments/assets/df2dd817-454d-4dd0-943c-0f315cb216ae)

- VFX is composed of 2 different effects. Arrows and a circle that goes away from the button. They both orient to face the camera

![image](https://github.com/user-attachments/assets/53776d25-e15a-4d4f-9653-7910bf805cde)

- Communicates with the BP_ChangingNumberManager

### BP_ChangingNumberManager

- First of all, I wanted to spawn everything in the editor but I was getting wierd result so I kept it simple with a BeginPlay setup.
- Spawn a set number of BP_ChangingNumber (explained later) and custom space between digits
- Have the logic to interact with every BP_ChangingNumber, lock them 1 by 1 or unlockinging them. have to role of counting the score of all the digit.

![image](https://github.com/user-attachments/assets/59d554e4-ca11-4fb9-9da4-f00201e808dc)

- Also checks if all the digits a the same for the special event (Confetti)

![image](https://github.com/user-attachments/assets/d923bee8-4225-4dbf-8d90-abed03e5d119)
![image](https://github.com/user-attachments/assets/648890eb-5255-411d-9fc6-324d472c014e)

- Send the values to the game manager 
![image](https://github.com/user-attachments/assets/fe7647da-b80e-46b5-ad98-1894e47de438)

### BP_ChangingNumberManager

- Spwans the main UI and keep track of the player score to send it to the UI

![image](https://github.com/user-attachments/assets/1bc5bbb7-4d08-4761-a083-e5318dbc89df)


### WBP_Score

- Display the player score (Bottom Left of the screen)

![image](https://github.com/user-attachments/assets/74b6779a-80e2-4538-a447-dc4f546b476f)

- Different visual effects 
- Add update the money score with a lerp

![image](https://github.com/user-attachments/assets/27e55a76-de20-4710-b466-48dca91f8b80)

- Add a dot every 3 digits to make the number more readable

![image](https://github.com/user-attachments/assets/15d00671-f0a1-46c9-84ab-0cfa37621ab0)

### WBP_Score

- Just a single digit switching every 0.2 seconds  

![image](https://github.com/user-attachments/assets/f37008b7-d6f2-4b97-8b58-751b84e7d1da)
![image](https://github.com/user-attachments/assets/cdbbec18-9439-46f6-9468-a7e2809f45f2)


## Why you chose this structure

- I was focused to make 2 elements scalable : the Player Interaction (with the interface) and the BP_ChangingNumberManager (Add a custom number of digits). If I had more time, I would have made a system to spend money to increase the number of digits you can have. The button would have been even more satisfying with bigger numbers.

- I overridden the FPS ABP because I wanted to add more animations espacially a hand slam for the last digit. So I could add a camera shake, an other VFX and SFX. In order to make the last press even more satisfying.

- For the sound, I made a bank for every sound classification to change the sound settings of every sound in a settings menu.

![image](https://github.com/user-attachments/assets/cbc8c8c1-f59e-44d0-ae9a-79db42f76b5f)

## What you did for optimization

- Avoid Casting (Usage of interfaces, direct references)
- Delete every usless assets in folders and in the map
- Make event calls (only in event tick when necessary)
- Particles not permanent. Niagara Systems may have a high number of particules (money drop) but I wanted to have fun with it. Still the value is clamped at 999 to avoid crashing.  
- Small textures and Materials (Unlit, Masked, User Interface)

## Anything else you think is important for us to know

### Niagara System : MoneyRain

Usage of collision, callbacks and user parameters

![image](https://github.com/user-attachments/assets/7703b7a1-d9ff-4594-82af-399cd39b8faa)
![image](https://github.com/user-attachments/assets/c31f784a-ac10-4e8f-966b-798157c930e6)

### Niagara System : ButtonPressing

Double VFX with a custom texture

![image](https://github.com/user-attachments/assets/aa1413ea-3bbd-43d0-ae6e-9173106a00c3)

### MovingGrid Shader (Ground)

Custom Made with parameters

![image](https://github.com/user-attachments/assets/462efdf7-8105-4c85-a7c2-52e213f3c662)

### Moving Cube Skybox 

3D cube with inverted normals and simple texture

![image](https://github.com/user-attachments/assets/0df0557b-8e5b-4ffb-b373-e38101b4bab0)

+ noise shader to add texture 

![image](https://github.com/user-attachments/assets/cfffd838-e36e-482c-8ee9-64ee1f410555)
