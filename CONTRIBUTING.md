# BakkesMod Template Contribution Guide

Each subheader outlines a task that needs to be done.

## imgui <> vcpkg

While all other dependencies and instances of `imgui` have been replaced with those coming from `vckpg`, there is still one notable dependency in `./BakkesPlugin/pch/pch.h`:
```c++
#include "imgui/imgui.h"
```
