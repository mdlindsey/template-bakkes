# BakkesMod Template Contribution Guide

Each subheader outlines a task that needs to be done.

## Memory leaks

It was mentioned that creating `cvars` with a constructor such as the example below causes memory leaks. This class pattern was adopted to improve syntax and control but should be redesigned to also ensure no memory leaks.

Sample of constructor-invoked, memory-leaking `cvar` from `./BakkesPlugin/plugin.cpp`:
```c++
new Cvar("hk_magic_num", 420, 69, 420, [=](string name, int newValue, int oldValue) {
    Log::Info("Updated MAGIC NUMBER to " + to_string(newValue));
});
```


## imgui <> vcpkg

While all other dependencies and instances of `imgui` have been replaced with those coming from `vckpg`, there is still one notable dependency in `./BakkesPlugin/pch/pch.h`:
```c++
#include "imgui/imgui.h"
```
