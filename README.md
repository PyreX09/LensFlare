# 🌟 LensFlare System

A **customizable and optimized Lens Flare System** for Roblox, built upon the original work by [@gluGPU](https://devforum.roblox.com/u/glugpu/summary).  
This modified version adds new features, fixes, and performance improvements for modern visual scripting and rendering.

![Roblox](https://img.shields.io/badge/Roblox-Module-blue?logo=roblox)
![Status](https://img.shields.io/badge/Status-Active-success)
![Language](https://img.shields.io/badge/Lua-5.1%2B-yellow)
![License](https://img.shields.io/badge/License-Fair--Use-lightgrey)

---

## 📥 Installation

To download LensFlare, go to the [**Releases**](https://github.com/PyreX09/LensFlare/releases) page.


---

## ⚙️ Features

✅ Full **OOP System** for lens flare control  
✅ **Dynamic color blending** based on object color and attributes  
✅ Built-in **LOD (Level of Detail)** support for optimization  
✅ **Raycast-based visibility detection** for realistic light occlusion  
✅ Simple API — create and destroy flares with just a few lines  
✅ Designed for **Cameras, Attachments, or Parts**

---

## 🚀 Usage Example

```lua
local on = false

script.Parent.Activated:Connect(function()
	if not on then
		on = true
		script.Parent.Light.Shadow.Enabled = true
		script.Parent.Light.Light.Enabled = true
		script.Parent.Light.Sound:Play()
		script.Parent.Front.SurfaceLight.Enabled = true
		
		script.Parent.LensFlare:SetAttribute("LensFlareDistance", 100)
		script.Parent.LensFlare:SetAttribute("LensFlareLOD", 1)
		script.Parent.LensFlare:SetAttribute("LensFlareStrength", 0.75)
		script.Parent.LensFlare:SetAttribute("LensFlareStyle", "Default")

	else
		on = false
		script.Parent.Light.Shadow.Enabled = false
		script.Parent.Light.Light.Enabled = false
		script.Parent.Light.Sound2:Play()
		script.Parent.Front.SurfaceLight.Enabled = false
		
		script.Parent.LensFlare:SetAttribute("LensFlareDistance", 0)
		script.Parent.LensFlare:SetAttribute("LensFlareLOD", 0)
		script.Parent.LensFlare:SetAttribute("LensFlareStrength", 0)
		script.Parent.LensFlare:SetAttribute("LensFlareStyle", "Default")
	end
end)
```

## 🧠 Developer Notes

Each flare runs on a render step bind, optimized to reduce redundant updates.

Uses cached attributes and properties for minimal overhead.

Built for first-person and cinematic scenes, tested up to 120 FPS, maybe.

## 👑 Special Thanks

[@gluGPU](https://devforum.roblox.com/u/glugpu/summary) : Creator of [LensFlare](https://create.roblox.com/store/asset/89532403908041/Lens-Flare-System) a system that I have spent countless hours modifying.

## ❓ Q&A
Q: How do I add a light to myself?
A: Do it like this 👇
	1. Add the Tag:** `LensFlare` to the object you want to have the flare effect.  
	2. Add the following Attributes:
 	  - `LensFlareDistance`
 	  - `LensFlareLOD`
 	  - `LensFlareStrength`
 	  - `LensFlareStyle`
	3. You can **set the values according to the example model in Workspace**, or tweak them yourself as you like.
