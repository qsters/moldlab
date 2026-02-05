![Moldlab Banner Image](./gitassets/banner.png)

MoldLab is a GPU-driven real-time simulation capable of supporting 1M agents simultaneously at 60fps or more, using compute shaders and a trail diffusion model.

The project was developed solo and shipped on **Steam** and **iOS**, focusing on performance, scalability, and interactive parameter exploration.

Inspired and expanded from Sebastian Lague’s video: [Coding Adventure: Ant and Slime Simulations](https://www.youtube.com/watch?v=X-iSQQgOd1A).


### Check it out in these places!
- **[Steam Store](https://store.steampowered.com/app/2454710/MoldLab/)**
- **[iOS Store](https://apps.apple.com/us/app/moldlab/id6449797910)**

## Quick Facts
- **Shipped to**: Steam + iOS
- **Engine:** Unity `2021.3.19f1` (LTS)
- **Languages:** C# (gameplay/tools), HLSL (Unity Compute Shaders)
- **Platforms shipped:** Steam (Windows, Mac, and Linux through Proton), iOS
- **Core tech:** GPU compute simulation + RenderTexture trail buffer

![Preview Gif 1](./gitassets/repelling-spores.GIF)

## In this game you
- Control millions of spores, recreating organic movement by following the pheromones left by other spores with a few specific rules.
- Through a few simple controls and values, completely change how the spores behave. Creating very satisfying and interesting movement by changing the agents ever so slightly.
- Customize the look of your screen with pre-made gradients as well as a custom gradient tool.

## About this project

I started building this project after watching the Sebastian Lague video linked above in Junior Year of Highschool. It inspired me to learn to code and make my first game. I started in rust making a custom pipeline that rendered out hundreds of images of simulation that would all be combined together to make a video. Needless to say, I had learned a lot by the time I got to shipping this game with Unity onto steam and iOS just when I was graduating from Highschool.

![Preview Gif 2](./gitassets/big-to-fine.GIF)

## Technical Overview
- Agent simulation on the GPU — spores are updated in parallel using compute kernels, avoiding CPU bottlenecks.
- Trail diffusion via RenderTexture — enables emergent pathfinding behavior through pheromone gradients.
- Parameter-driven simulation — ScriptableObjects allow real-time tuning without recompilation.
- Minimal CPU and GPU synchronization — reduces stalls and keeps frame times stable at high agent counts. I worked really hard on this one.

On modern hardware this is optimized enough it can run **tens of millions** of spores smoothly (gpu and resolution dependent). I cap it to 1 million spores in game as that is all you need at the resolutions most people have (if you have an 8k display then you are the odd one out!).

### Where to look in the code
- Compute kernels: `Assets/Scripts/ComputeShaders/`
- C# orchestration: `Assets/Scripts/Simulation.cs`
- GPU dispatch helpers: `Assets/Scripts/Helpers/ComputeHelper.cs`
- Tunable settings: `Assets/Scripts/ScriptableObjects/SimulationDataScriptableObject.cs`

![Preview Gif 3](./gitassets/exploding-spores.GIF)

## Run Locally
1. Install Unity Hub + Unity `2021.3.19f1`
2. Open this folder as a project
3. Open the tutorial scene under `Assets/Scenes/`
4. Press Play

## Notes
- Mobile build includes Ads integration.
- Steam build includes Steamworks integration.
- PR's are welcome! I would be open to releasing new features to steam if they come up.

## If you like this

See my [MoldLab-3D](https://github.com/qsters/moldlab-3d) project for a 3d version of this I coded up in a few months at the end of 2025 as my first C++ project.

## License
Apache-2.0 (see `LICENSE`).