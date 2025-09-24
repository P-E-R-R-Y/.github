# Libraries

Library | Classes
--- | ---
Static | Abstract(can be Interface)/Concrete
Shared | Implementation(can be Encapsulation)

## Static
- **Concrete** classes are use to define standard type or not abstract classes (*not yet* or *not required*) like .

- Abstraction are use to define

- **Interface** classes are use to define Patterns like IWindow gives RaylibWindow, SfmlWindow, by encapsulating Raylib or SFML.

## Shared

- **Encapsulation** is used to develop an app or anything using the interface and depending on the initialisation of the interface it will use raylib or sfml, avoiding dependencies. by giving the possibility to change concrete class used.

## Example

> This way you avoid depending on raylib or any library.

Before:

```c
Game -> Raylib
```

After:

```c
Game -> IGraphic -> RayGraphic -> Raylib
                 -> SfmlGraphic -> Sfml
                 -> ...
```
