# Parallax Juicy Button

Challenge done in 1 week (I wasn't available the first week)

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
