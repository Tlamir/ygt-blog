+++
title = "Why AI Needs More Modern Open Game Projects"
date = 2026-07-22
description = "What using AI in a real Godot project reveals about the lack of complete modern open game projects."
tags = ["AI", "Game Development", "Godot", "Game Engines", "Open Source"]
+++

AI can write game code, but game development is more than code.

I am developing my own 3D game in Godot while experimenting with AI coding agents.

In my project, AI performs well when a task is narrow and easy to verify. Once the task requires visual judgment, game feel, balance or an understanding of the whole project, the quality drops quickly.

That made me question what material AI has learned from. We have open engines, documentation, tutorials, isolated scripts and older source releases. What we rarely have are complete modern game projects developed in public.

I think that gap is part of the problem.

## Open engines are only the start

[Godot is open source under the MIT licence](https://godotengine.org/license/). [Unreal Engine provides source access through Epic](https://dev.epicgames.com/documentation/en-us/unreal-engine/downloading-source-code-in-unreal-engine), while [Unity offers source access under commercial plans](https://unity.com/products/source-code).

This gives us engine code for rendering, physics, animation, input, audio and editor systems.

It does not give us the complete project behind a finished game.

An engine shows how the tools work. A game project shows how developers used those tools to build combat, levels, UI, progression, custom tools and content.

We need both.

## Public game code

[Quake III Arena](https://github.com/id-Software/Quake-III-Arena) and [Doom 3 BFG](https://github.com/id-Software/DOOM-3-BFG) are important official source releases. They contain real production rendering, gameplay and engine code.

EA has also released source for classic Command & Conquer games, including [Tiberian Dawn](https://github.com/electronicarts/CnC_Tiberian_Dawn), [Red Alert](https://github.com/electronicarts/CnC_Red_Alert) and [Generals with Zero Hour](https://github.com/electronicarts/CnC_Generals_Zero_Hour).

Community projects help fill some of the gap. [OpenRCT2](https://github.com/OpenRCT2/OpenRCT2) is an open source reimplementation of RollerCoaster Tycoon 2. The re3 and reVC projects reverse engineered GTA III and Vice City into working C++ projects, with [community mirrors preserving the code](https://github.com/Jai-JAP/re-GTA).

These projects are valuable, but most are older games, partial releases or community reconstructions.

We have almost no comparable official public projects for modern AAA titles such as GTA V, Elden Ring, Cyberpunk 2077 or Monster Hunter.

I know these are extreme examples, but you get the point. Complete modern game projects are rarely public.

We cannot study their complete gameplay systems, scenes, UI, animation graphs, internal tools, balance history or development process.

Having access to an engine does not give us the game built with it.

## My experience using AI in game development

These are real examples from trying to use AI in my own game development workflow.

AI is good at clear technical tasks. It successfully found a sound on [Freesound](https://freesound.org/), downloaded it, cut the section I needed and implemented it in the game. I was impressed by how well it handled the full task.

It can also implement game features quickly when I already know what the feature should do.

Basic UI is possible, but it needs a strict Markdown guide and an existing theme to follow. Otherwise, the result quickly turns into generic AI slop. Borders, spacing, typography and transitions need clear rules.

It can create simple animations. They are not perfect, but they can work as a starting point.

I started using report Markdown files after seeing the workflow in a [Cherno video](https://www.youtube.com/watch?v=A4aLYwtpyes&t). Codex handles them well. It can record what changed, what still needs work and what the next agent should know.

I also keep asset licences in a separate Markdown file. Codex can update it when it downloads, edits or adds an asset.

## Where it fails

I tried to create an environment using an existing asset pack. The agent spent too much time and too many tokens searching through the assets, but the final environment was still bad.

I also asked it to improve the lighting, fog and atmosphere. It could change the values, but it could not produce an acceptable visual result.

Visual work still needs strong human art direction.

I once asked it to create a simple credits screen. It was a straightforward task, but the result became a huge pile of AI slop instead of something that felt like game credits.

Any regular gamer could explain roughly how credits should look and flow. The AI could not reach that basic level without detailed instructions.

Game design and balance are even less reliable. AI can suggest decent ideas, but the implementation often misses the purpose of the mechanic or breaks the balance. It handles vague direction poorly.

Never let AI take the direction.

It should help implement your decisions, not decide what the game should be.

## What the research shows

I looked into recent research on AI agents in game engines to see whether these problems were only happening in my project. The papers I found report similar results: AI performs much worse as projects become larger, more visual and more connected.

[JAMER](https://arxiv.org/abs/2606.19830) searched more than 240,000 repositories to build a dataset of real Godot projects. Only 8,133 were usable after checking whether they were valid, complete and runnable. Many were small game jam projects because complete public game projects are difficult to find.

AI performance dropped heavily on larger projects. Runtime pass rates fell from 80.4 percent on small tasks to 5.7 percent on large ones. Making the code compile did not mean the game behaved correctly.

[GameDevBench](https://arxiv.org/abs/2602.11103) found that visual Godot tasks were harder than gameplay coding tasks. Screenshots and video feedback improved the results.

[GameCraft-Bench](https://arxiv.org/abs/2606.17861) found a similar pattern when agents created complete games. They could produce recognizable mechanics but struggled with visual feedback, content and presentation.

These findings are close to what I experienced. AI can handle a clear feature, but it struggles when it needs to understand and judge the whole game.

## What is missing

Open engines and isolated scripts are not enough. We need more complete modern game projects that show how code, scenes, assets, tools and design decisions work together.

These projects would help both AI and developers learn from real production instead of disconnected examples.

AI should support implementation. The developer must keep control of the architecture, game design, art direction and overall direction.
