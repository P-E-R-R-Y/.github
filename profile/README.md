# Wiki (P-E-R-R-Y)

<details>
<summary>
Libraries
</summary>

### Static

- Concrete classes are use to define standard type or not abstract classes (not yet or not required) like .

- Interface classes are used in a Patterns where IWindow gives RaylibWindow, SfmlWindow, by encapsulating Raylib or SFML.

### Shared

- Encapsulation is used to develop an app or anything using the interface and depending on the initialisation of the interface it will use raylib or sfml, avoiding dependencies. by giving the possibility to change concrete class used.

### Example

> This way you avoid depending on raylib or any library.

Before:
```
Game -> Raylib
```
After:
```
Game -> IGraphic -> RayGraphic -> Raylib
                 -> SfmlGraphic -> Sfml
                 -> ...
```
</details>

<details>
<summary>
Module
</summary>

The Module is a flexible interface layer that lets you load, manage, and interact with modules without knowing their concrete implementation.

Like a computer stores files it doesn’t understand, this system can handle modules dynamically, letting them act, be used, or interact with others while keeping their internal behavior hidden.

ModuleRegistry tracks modules by type and allows switching the active module, enabling seamless extensibility and runtime flexibility.

Modules are like files on a computer: each has a name and type, but the system itself doesn’t need to fully understand them. Just like .exe or .doc can be executed or read directly, other files (.pdf, .png, .obj) require a specific application to use them. Similarly, a module can represent an Application, Graphic Library, Network Library, or any component—usable by other modules without knowing all its internal details.


### Pattern Overview

```
DLL
 │
 │ createModule()
 ▼
IModule*
 │
 │ dynamic_cast
 ▼
IGraphicModule*  <-------------------->  SfmlGraphicModule*
 │                                          (concrete)
 │ GetWindow()                              
 ▼
IWindow*  <---------------------------->  SfmlWindow*
```

### Explanation

1. **DLL** provides `createModule()` → returns `IModule*`.  
2. **ModuleRegistry** stores `IModule*` and retrieves by type.  
3. Cast to **type-specific interface** (example: `IGraphicModule*`) to access specialized features.  
4. **Concrete implementations** are hidden behind interfaces.  
5. Sub-objects (example: `IWindow*`) are returned as interface pointers, hiding the real type (`SfmlWindow*`).

</details>

## Libraries

### Basics

- [x] CMake
- [x] FetchDependencies (using FindPackage)
- [x] Test (GoogleTest)
- [ ] CMakeUtils -> ToolBSL 
- [ ] HunterV3 using IModule + ECS + IGraphic,IApp + ImpGraphic(optionally ImpApp which could be the game).

### Static Concrete

- [x] system
- [x] maths
- [ ] ecs

### Static Interface

- [x] imodule (IModule)
- [x] igraphic (IGraphicModule)
  - [ ] feat (SoundBuffer, Texture, Font)
- [x] iapp (IAppModule)
- [ ] inetwork (INetworkModule)

### Shared Implementation</summary>

- [x] raygraphic (RayGraphicModule)
- [x] sfmlgraphic (SfmlGraphicModule)
- [ ] sdlgraphic (SdlGraphicModule)
- [ ] hunterapp (HunterAppModule)
- [ ] asionetwork (AsioNetworkModule)

## Testing

- [x] GTest

```
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release \
&& cmake --build build --clean-first \
&& ctest --test-dir build --output-on-failure
```

## CI

- [x] compile & play GTest
- [x] play GTest with graphical environement (see raygraphic or sfmlgraphic)

## Documentation

- [x] org wiki
- [ ] generate doxygen on repository
- [ ] merge doxygen on organisation.
- [ ] ci - cron to update it every day.
