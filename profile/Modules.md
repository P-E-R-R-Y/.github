# Module System

The Module is a flexible interface layer that lets you load, manage, and interact with modules without knowing their concrete implementation.

Like a computer stores files it doesn’t understand, this system can handle modules dynamically, letting them act, be used, or interact with others while keeping their internal behavior hidden.

ModuleRegistry tracks modules by type and allows switching the active module, enabling seamless extensibility and runtime flexibility.

Modules are like files on a computer: each has a name and type, but the system itself doesn’t need to fully understand them. Just like .exe or .doc can be executed or read directly, other files (.pdf, .png, .obj) require a specific application to use them. Similarly, a module can represent an Application, Graphic Library, Network Library, or any component—usable by other modules without knowing all its internal details.


# Module Pattern Overview
```
DLL
 │
 │ createModule()
 ▼
IModule*
 │
 │ dynamic_cast
 ▼
IGraphicModule*  <-------------------->  SfmlGraphicModule
 │                                          (concrete)
 │ GetWindow()                              
 ▼
IWindow*  <---------------------------->  SfmlWindow
```

### Explanation

1. **DLL** provides `createModule()` → returns `IModule*`.  
2. **ModuleRegistry** stores `IModule*` and retrieves by type.  
3. Cast to **type-specific interface** (`ITypeModule*` or `IGraphicModule*`) to access specialized features.  
4. **Concrete implementations** are hidden behind interfaces.  
5. Sub-objects (like `IWindow*`) are returned as interface pointers, hiding the real type (`SfmlWindow*`).  