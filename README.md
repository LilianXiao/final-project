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
It's a little goofy to keep updating the .blend file, but here are some screenshots and a video demo of the current visualizer in Blender.  This is a standard horizontal cube visualizer, and I created a procedural noise shader for the coloring.  I may consider making a "spherical" visualizer with a mesh that deforms based on the music sample.

The shader itself makes use of blending voronoi + fbm noise and offsetting color, emission, distortion, and detail parameters using time (frame) + sine functions.  This is currently being rendered in eevee, but I'd like to figure out how to add some subtle bloom/glow.

<img width="650" height="398" alt="image" src="https://github.com/user-attachments/assets/e2c31637-4f69-40dd-b842-afc71e7dd824" />

<img width="642" height="390" alt="image" src="https://github.com/user-attachments/assets/8ccbcc44-503c-4332-9fad-dab04b91f309" />

<img width="863" height="653" alt="image" src="https://github.com/user-attachments/assets/a330616f-abd5-430d-a856-c91917cb767b" />

Short video demo:
https://drive.google.com/file/d/1Azspsej8MV49RC9JZOpfTU-JfBLviWNv/view?usp=sharing

As an update, I may not actually end up using this visualizer component, if I end up making a lot of progress in my shadertoy!

## Milestone 2: Implementation part 2 (due 11/24)
I worked on creating the visualizer background; the main inspiration is from DV-i's original dj set video, which the song I'm using (resonance) is included in.

https://www.shadertoy.com/view/W3Bfzd

<img width="469" height="260" alt="image" src="https://github.com/user-attachments/assets/9581055b-9cd8-43fc-92b0-c6318f37d204" />

<img width="465" height="262" alt="image" src="https://github.com/user-attachments/assets/efff010c-ec00-4783-afe7-74625a39cbd5" />

I used the texture function on the music channel so I could find frequency/amplitude, then overlaid it with a noise generator + fbm to give it somoe more visual grunge.

To figure out how to make an actual wave using the audio texture, I referenced (the goat) iq's input-sound work.  Shadertoy stores sound as a 512 x 2 resolution texture, where there are 2 "strips" (fft and waveform).
To get the "wave visualizer" I fetch the waveform data at each index using texelFetch (texelFetch is raw integer texel coordinates, so I use this instead of just texture, which does normalized coordinates and additional filtering).

<img width="473" height="259" alt="image" src="https://github.com/user-attachments/assets/825dc51f-b72c-4676-a340-cb8a80d24ddf" />

<img width="472" height="263" alt="image" src="https://github.com/user-attachments/assets/2e84b7f0-9028-4890-b5ef-3ee8e17c5076" />

Next I will be working on making the shadertoy more complex, making some animated sdfs and additional visual effects, and compositing everything together for the final submission.

## Final submission (due 12/1)
There are now four main layers to the shadertoy: an inverted fbm video pass, a sobel filter pass, an animated SDF pass with additional fbm post processing, and the main image (which contains the main music visualizer component as well as a fun little speaker sdf that is animated using the amplitude of the waveform).  I created multiple buffers and transferred their outputs to my main image using the channels; additionally, I am using the shadertoy web extension Custom Textures (https://chromewebstore.google.com/detail/shadertoy-custom-texures/jgeibpcndpjboeebilehgbpkopkgkjda), which allows one to drop in images, video mp4s, and soundfiles into channels as textures.  This adds another level of customizability for the visuals!

Some more details on implementation:
- To achieve the noisy aberration effect on some passes, I offset the uvs by fbm noise with sine of time to cause the shifting
- I referenced iq's sdfs and my earlier work with the procedural faces lab to make the animated sdfs.  They oscillate using sine on time, as well as changing size so it looks like they're zooming in and out
- To make the "speaker" sdf I created three sdf spheres, with the concave speaker being the result of smoothSubtraction between two slightly offset spheres.  I thought it was nice to do size deform using the input sound waveform amplitude; it looks a little like something you'd see in an early animusic video haha

The compositing part of everything is just mixing the layers and doing some fine tuning with blending and frequency parameters so the visuals can all be seen.  I really think that the early 2000's hypermedia basement dj party vibe is captured by the combination of these visuals!  Again, a lot of inspiration from psychoangel and their dj set visualizers.

Some demo snippets! (kinda compressed so I can embed them here and the quality is rather low, but there are some short mp4s in the repo itself!)

https://github.com/user-attachments/assets/e508f853-ff3b-444c-af7e-1c73594ec44f

https://github.com/user-attachments/assets/7e7530f6-c62a-4f32-8c35-9ecf47d4d6a9

https://github.com/user-attachments/assets/41ccf098-886f-4327-bf5f-3e9a38423c44

<img width="1158" height="648" alt="Screenshot 2025-12-01 214906" src="https://github.com/user-attachments/assets/423c3d8e-a4b6-41b0-a5e0-40ba80d8ae68" />

<img width="1310" height="730" alt="Screenshot 2025-12-01 214839" src="https://github.com/user-attachments/assets/8483ffee-a864-4d18-a8fc-deda941a5b14" />

<img width="1311" height="727" alt="Screenshot 2025-12-01 214829" src="https://github.com/user-attachments/assets/84956e14-3f39-4b1f-812c-cd15a2207efe" />

## Post mortem thoughts
I ended up scrapping the component I made in Blender, because I decided I wanted to try implementing everything in my shadertoy; I also ended up deciding that the blender visualizer wouldn't really add a lot to the shadertoy visualizer, which is why I ended up focusing on my shadertoy for the rest of the process.  However, I still took some inspiration from when I tinkered around with the blender visualizer in milestone 1.
I'd like to make a full render on some demo dj set, either one I like online or just a couple songs I enjoy whipped together.  However, this recording may take a while, so I'll likely try to add that sometime later.  In the meantime, I'm very happy with how my music visualizer tool turned out!  It was a great learning experience with making multipass shaders, using multiple buffers and channels, as well as putting together a lot of the procedural skills I learned over the course of 5660.
