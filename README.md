# Final Project!

This is it! The culmination of your procedural graphics experience this semester. For your final project, we'd like to give you the time and space to explore a topic of your choosing. You may choose any topic you please, so long as you vet the topic and scope with an instructor or TA. We've provided some suggestions below. The scope of your project should be roughly 1.5 homework assignments). To help structure your time, we're breaking down the project into 4 milestones:

## Project planning: Design Doc (due 11/5)
Before submitting your first milestone, _you must get your project idea and scope approved by Rachel, Adam or a TA._

### Design Doc
Start off by forking this repository. In your README, write a design doc to outline your project goals and implementation plan. It must include the following sections:

#### Introduction
All around us is cool music...but in the hands of a DJ, music can become a much more immersive experience.  We can go a step further and imagine MVs for songs, remixes, games, and more; all with colorful and expressive components that follow the tempo and beat.  Having been thoroughly intrigued by many cool visualizers and music videos in general over the years, I find this idea too inticing to pass up.

#### Goal
I intend on creating a short music video for a personal music mix (we'll see how far we get haha), consisting of music from DV-i, Psychoangel, Metaroom, and Machine Girl (depending on how much time I have, I may end up just doing it for one piece).  All these artists share something in common; that is heavy use of sampling, breakbeats (sometimes), electronic music/synths, and whatever you can imagine for a techno rave scene.  I will start off attempting to build a visualizer and work with Resonance by DV-i, then add in some more post-processing and create a nice composite video.

#### Inspiration/reference:
Here are some sources for excellent points of inspiration!
- https://www.youtube.com/watch?v=uxeE8zpwsqw
- https://www.youtube.com/watch?v=TDoQDcm4hIQ
- https://www.youtube.com/watch?v=btTH2bz_eg8
- https://www.youtube.com/watch?v=ure6OT0LwtM
- https://www.youtube.com/watch?v=-YAWcks7kOg
- https://www.youtube.com/watch?v=E-kVV_5_Th4

#### Specification:
- A "central" visualizer, involving something that very clearly visually follows the audio sample
- Animated 3D annd 2D components
- Possibly elements of traditional animation
- Post-processing effects (for more eye candy really)

#### Techniques:
As a 3D modeler, I will most likely be making a lot of things in Blender.  Blender is great because you have avenues for both 3D modeling and 2D/3D animation, as well as a lot of opportunities for proceduralism (such as geometry nodes or creating a shader/material) (a lot of potential with metaballs and physics sims as well!).  I will use ShaderToy to create background effects and visualizer components (also because I want to do some fun stuff with sdfs!); additional post-processing overlays can be done using art programs and software like DaVinci Resolve, which I will also be using to make the final composite.  Though I'm a beginner with TouchDesigner, I think it could be great to explore.

#### Design:
Blender render + Shadertoy + traditionally animated composite; will make use of video editing software for compositing and some extra post-processing.

#### Timeline:
- I make a da video


## Milestone 1: Implementation part 1 (due 11/12)
It's a little goofy to keep updating the .blend file, but here are some screenshots and a video demo of the current visualizer in Blender.  This is a standard horizontal cube visualizer, and I created a procedural noise shader for the coloring.  However, because this method of visualizer makes use of a Blender add-on, I am also working on a "spherical" visualizer with a mesh that deforms based on the music sample.

The shader itself makes use of blending voronoi + fbm noise and offsetting color, emission, distortion, and detail parameters using time (frame) + sine functions.  This is currently being rendered in eevee, but I'd like to figure out how to add some subtle bloom/glow.

<img width="650" height="398" alt="image" src="https://github.com/user-attachments/assets/e2c31637-4f69-40dd-b842-afc71e7dd824" />

<img width="642" height="390" alt="image" src="https://github.com/user-attachments/assets/8ccbcc44-503c-4332-9fad-dab04b91f309" />

<img width="863" height="653" alt="image" src="https://github.com/user-attachments/assets/a330616f-abd5-430d-a856-c91917cb767b" />

Short video demo:
https://drive.google.com/file/d/1Azspsej8MV49RC9JZOpfTU-JfBLviWNv/view?usp=sharing


## Milestone 2: Implementation part 2 (due 11/24)
I worked on creating the visualizer background; the main inspiration is from DV-i's original dj set video, which the song I'm using (resonance) is included in.

https://www.shadertoy.com/view/W3Bfzd

<img width="469" height="260" alt="image" src="https://github.com/user-attachments/assets/9581055b-9cd8-43fc-92b0-c6318f37d204" />

<img width="465" height="262" alt="image" src="https://github.com/user-attachments/assets/efff010c-ec00-4783-afe7-74625a39cbd5" />

I used the texture function on the music channel so I could find frequency/amplitude, then overlaid it with a noise generator + fbm to give it somoe more visual grunge.

Next I will be working on making my blender visualizer more complex, making some animated sdfs and additional visual effects, and compositing everything together for the final submission.

## Final submission (due 12/1)
Time to polish! Spen this last week of your project using your generator to produce beautiful output. Add textures, tune parameters, play with colors, play with camera animation. Take the feedback from class critques and use it to take your project to the next level.

Submission:
- Push all your code / files to your repository
- Come to class ready to present your finished project
- Update your README with two sections 
  - final results with images and a live demo if possible
  - post mortem: how did your project go overall? Did you accomplish your goals? Did you have to pivot?

## Topic Suggestions

### Create a generator in Houdini

### A CLASSIC 4K DEMO
- In the spirit of the demo scene, create an animation that fits into a 4k executable that runs in real-time. Feel free to take inspiration from the many existing demos. Focus on efficiency and elegance in your implementation.
- Example: 
  - [cdak by Quite & orange](https://www.youtube.com/watch?v=RCh3Q08HMfs&list=PLA5E2FF8E143DA58C)

### A RE-IMPLEMENTATION
- Take an academic paper or other pre-existing project and implement it, or a portion of it.
- Examples:
  - [2D Wavefunction Collapse Pokémon Town](https://gurtd.github.io/566-final-project/)
  - [3D Wavefunction Collapse Dungeon Generator](https://github.com/whaoran0718/3dDungeonGeneration)
  - [Reaction Diffusion](https://github.com/charlesliwang/Reaction-Diffusion)
  - [WebGL Erosion](https://github.com/LanLou123/Webgl-Erosion)
  - [Particle Waterfall](https://github.com/chloele33/particle-waterfall)
  - [Voxelized Bread](https://github.com/ChiantiYZY/566-final)

### A FORGERY
Taking inspiration from a particular natural phenomenon or distinctive set of visuals, implement a detailed, procedural recreation of that aesthetic. This includes modeling, texturing and object placement within your scene. Does not need to be real-time. Focus on detail and visual accuracy in your implementation.
- Examples:
  - [The Shrines](https://github.com/byumjin/The-Shrines)
  - [Watercolor Shader](https://github.com/gracelgilbert/watercolor-stylization)
  - [Sunset Beach](https://github.com/HanmingZhang/homework-final)
  - [Sky Whales](https://github.com/WanruZhao/CIS566FinalProject)
  - [Snail](https://www.shadertoy.com/view/ld3Gz2)
  - [Journey](https://www.shadertoy.com/view/ldlcRf)
  - [Big Hero 6 Wormhole](https://2.bp.blogspot.com/-R-6AN2cWjwg/VTyIzIQSQfI/AAAAAAAABLA/GC0yzzz4wHw/s1600/big-hero-6-disneyscreencaps.com-10092.jpg)

### A GAME LEVEL
- Like generations of game makers before us, create a game which generates an navigable environment (eg. a roguelike dungeon, platforms) and some sort of goal or conflict (eg. enemy agents to avoid or items to collect). Aim to create an experience that will challenge players and vary noticeably in different playthroughs, whether that means procedural dungeon generation, careful resource management or an interesting AI model. Focus on designing a system that is capable of generating complex challenges and goals.
- Examples:
  - [Rhythm-based Mario Platformer](https://github.com/sgalban/platformer-gen-2D)
  - [Pokémon Ice Puzzle Generator](https://github.com/jwang5675/Ice-Puzzle-Generator)
  - [Abstract Exploratory Game](https://github.com/MauKMu/procedural-final-project)
  - [Tiny Wings](https://github.com/irovira/TinyWings)
  - Spore
  - Dwarf Fortress
  - Minecraft
  - Rogue

### AN ANIMATED ENVIRONMENT / MUSIC VISUALIZER
- Create an environment full of interactive procedural animation. The goal of this project is to create an environment that feels responsive and alive. Whether or not animations are musically-driven, sound should be an important component. Focus on user interactions, motion design and experimental interfaces.
- Examples:
  - [The Darkside](https://github.com/morganherrmann/thedarkside)
  - [Music Visualizer](https://yuruwang.github.io/MusicVisualizer/)
  - [Abstract Mesh Animation](https://github.com/mgriley/cis566_finalproj)
  - [Panoramical](https://www.youtube.com/watch?v=gBTTMNFXHTk)
  - [Bound](https://www.youtube.com/watch?v=aE37l6RvF-c)

### YOUR OWN PROPOSAL
- You are of course welcome to propose your own topic . Regardless of what you choose, you and your team must research your topic and relevant techniques and come up with a detailed plan of execution. You will meet with some subset of the procedural staff before starting implementation for approval.
