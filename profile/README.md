# 🌟 P-E-R-R-Y   

A **C++ development kit** to build games and applications from scratch, without Unity/Unreal.  
Provides **core libraries**, **interfaces**, and **implementations** so you can focus on building your app instead of plumbing.
Build & Tested on macos M2, and tested with ci on ubuntu (even graphical lib XD).

---

## ✨ Overview

`P-E-R-R-Y DevKit` is a modular C++ devkit that provides:

- **Static libraries** for core systems:
  - [x] system
  - [x] maths
  - [x] [ecs (Entity Componennt System)](https://p-e-r-r-y.github.io/ecs)
  - [x] [i18n (Internationalisation)](https://p-e-r-r-y.github.io/i18n)
  - [x] procedurals (perlin noise, automates cellulaires, random walks, L systems, Bruit fractal, Graph/Tree )

- **Interface modules** (`IModule`, `IGraphicModule`, `IAppModule`) to abstract platform and library dependencies.  
  - [x] imodule
  - [x] igraphic
  - [x] iapp

- **Concrete implementations** for graphics (Raylib, SFML), apps, and optional network modules.  
  - [x] raygraphic
  - [x] sfmlgraphic
  - [ ] sdlgraphic (need rework from P-E-R-R-Y/PERRY)
  - [ ] openglgraphic

- **Testing tools** 
  - [x] CXX17+ GoogleTest. usualy CXX20 (the belovel version)
  - [x] CXX17- HandMades. usualy CXX11 (the legacy version)

- **Flexible module system** to swap components dynamically.

Think of it as a **C++ game/app starter kit**: you get the essentials pre-built, but everything is modular and customizable.

---

## 🏗️ How It Works

<details>
<summary>1️⃣ Static Libraries</summary>

These are **ready-to-use C++ libraries** that don’t depend on any runtime frameworks:

- **System** – Platform abstraction (file, time, logging).  
- **Maths** – Vector, matrix, random utilities.  
- **ECS** – Entity Component System for game objects and logic.
- **i18n** – Internationalization library for multi-language support.  
</details>

<details>
<summary>2️⃣ Interface Modules</summary>

Define abstract **interfaces** so your code doesn’t depend on specific libraries:

- **IModule** – Base module interface.  
- **IGraphic** – Abstract graphics interface. Supports multiple backends (Raylib, SFML, SDL).  
- **IApp** – Abstract application interface for windowing and lifecycle.  
- **INetwork** – Abstract networking (foreseen).

> This allows you to write **generic code** without binding to Raylib, SFML, or any other library.
</details>

<details>
<summary>3️⃣ Implementations</summary>

Concrete modules implement the interfaces:

- **RayGraphic** – Uses Raylib for graphics.  
- **SfmlGraphic** – Uses SFML for graphics.  
- **SfmlGraphic** – Uses SFML for graphics. (need rework from P-E-R-R-Y/Perry)
- **HunterApp** – Example application.  
- **AsioNetwork** – Networking with Asio (foreseen).
</details>

<details>
<summary>4️⃣ Module Registry</summary>

The `ModuleRegistry` keeps track of all modules and lets you **switch implementations at runtime**:

```text
Game -> IGraphicModule -> RayGraphicModule -> Raylib
                          -> SfmlGraphicModule -> SFML
