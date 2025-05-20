# Parallax Juicy Button

## Controls

Move - WASD / Arrows
Look - Mouse
Interact - LMB (Press or Hold)

Goal - Score the highest number 

## Main features

- 1 player (Animations + Interaction)
- 1 button
- 1 Changing number widget
- 1 Score counter widget
- 3 VFX (Confetti / Money rain / Button press)
- 4 SFX + 1 BGM (FMOD Integration)

## How the project is structured

# Player
- The player uses the a Input Map Control + Input Asset
- Left click plays a custom animation 
- Player Model is base arm from UE5 
- Took the original Animation blueprint. Deleted everthing useless and added logic over it
- Made a custom pressing button animation via AI (Quickmagic AI)

- Animation montage with notifies for the code + montage section to spam the animation (Hold LMB)
- Sphere Trace to detect if any thing can be interacted (via an interface to avoid casting)


# Button

- Interactible interface inmplementation with an onPressed event
- when pressed play SFX + vfx + animation
- SFX have a random pitch + a higher pitch each time its pressed

![image](https://github.com/user-attachments/assets/df2dd817-454d-4dd0-943c-0f315cb216ae)


