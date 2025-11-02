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

## ❓ Q&A (Extended)

### Q: How do I add a light to myself?
**A:**  
Do it like this 👇

1. **Add the Tag:** `LensFlare` to the object you want to have the flare effect.  
2. **Add the following Attributes:**
   - `LensFlareDistance`
   - `LensFlareLOD`
   - `LensFlareStrength`
   - `LensFlareStyle`
3. You can **set the values according to the example model in Workspace**, or tweak them yourself as you like.

---

### Q: What is `NUMBER_OF_RAYCASTS`?
**A:**  
This determines how many rays are shot to detect flare obstruction.  
- Lower values → faster performance, less accurate occlusion.  
- Higher values → slower performance, more precise flare visibility.

---

### Q: What does `RAYCAST_RADIUS` do?
**A:**  
It spreads out the rays around the flare source. Doesn’t affect performance, just changes flare obstruction detection area.

---

### Q: How does `TRANSPARENCY_THRESHOLD` work?
**A:**  
Parts more transparent than this value won’t block lens flares.  
- 1 → even fully transparent parts block flares.  
- 0 → only opaque parts block flares.

---

### Q: How is sun flare strength determined?
**A:**  
Sun flare is based on:
- `SUN_ANGLE_THRESHOLD` → angle above horizon to start fading  
- `SUN_BRIGHTNESS_THRESHOLD` → Lighting.Brightness value for full strength  
- `SUN_EXPOSURE_ADJUSTMENT` → exposure change when looking directly at sun  
- `SUN_EXPOSURE_TIME` → duration of smooth exposure adjustment  

---

### Q: What does `LensFlareLOD` affect?
**A:**  
LOD (Level of Detail) scales flare quality based on distance.  
- Higher LOD → flares stay detailed farther away  
- Lower LOD → distant flares simplify/fade sooner  

---

### Q: What is `LensFlareStrength`?
**A:**  
Determines how visible/bright a flare is.  
- 0 → invisible  
- 1 → full brightness  

---

### Q: What is `LensFlareDistance`?
**A:**  
Maximum distance at which a flare is visible.  
- Flare disappears if camera is farther than this value.

---

### Q: How does the system handle dynamic raycasts?
**A:**  
If LOD is enabled, the number of rays is recalculated based on distance.  
- Closer → more rays → accurate obstruction  
- Farther → fewer rays → performance optimized  

---

### Q: Can I make a sun lens flare?
**A:**  
Yes. Create a Part, set `IsSunFlare = true` and give it `LensFlareDistance` and `LensFlareStrength`.  
The module automatically updates position, strength, and exposure based on Lighting and camera.

---

### Q: How does debug mode work?
**A:**  
If `DEBUG_MODE = true`, the console prints:
- Part name  
- Flare alpha  
- Number of rays hitting  
- Distance to camera  
- LOD recalculations  
- Re-emission events  

It’s useful for tweaking flare behavior during development.
