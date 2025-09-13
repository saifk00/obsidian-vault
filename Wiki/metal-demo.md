Some notes on my usage of the metal framework in the middle weeks of September 2025
# Metal Learning Checkpoints

## ✅ Checkpoint 1: First Triangle
- **Action:** Drew a simple triangle.  
- **Confusion:** Why does the vertex `position` need to be a `float4`?  
- **Resolution:** Learned that Metal uses **homogeneous clip-space coordinates**; 4 components are required for proper transformations.

---

## ✅ Checkpoint 2: From Triangle to Quad
- **Action:** Extended rendering to quads using **indexed primitive draws**.  
- **Confusion:** Why is (0,0) not the bottom-left corner of the screen?  
- **Resolution:** Discovered that Metal’s **NDC (Normalized Device Coordinates)** differ from pixel coordinates; (0,0) is the screen center.

---

## ✅ Checkpoint 3: Fragment Shading Experiments
- **Action:** Made fragment colors depend on:
  - Interpolated vertex values (gradients).  
  - Fragment coordinates (procedural color).  
- **Confusions:**  
  - Unexpected translucency.  
  - x-values “growing too fast.”  
- **Resolution:** Learned how **varyings** are interpolated between vertex and fragment stages, and how fragment coordinates map into shader space.

---

## ✅ Checkpoint 4: Managing State in Swift
- **Action:** Added bindings and state for selecting demos.  
- **Confusion:** Ran into “using `self` before initialization” errors.  
- **Resolution:** Learned Swift’s **property initialization rules** and the need to set up state in the right order.

---

## ✅ Checkpoint 5: Encoders and Buffers
- **Action:** Worked with command encoders and data buffers.  
- **Confusions:**  
  - Why do encoders/buffers need explicit management?  
  - Why must pipeline state be rebound every time?  
- **Resolution:**  
  - Encoders = define GPU **command sequences** explicitly.  
  - Buffers = raw memory blocks bound to shaders.  
  - APIs are strict so GPU execution is deterministic, parallel, and optimizable.

---

## ✅ Checkpoint 6: Separation of Concerns
- **Action:** Organized code so different demos shared the same loop but swapped pipelines/shaders.  
- **Resolution:** Saw the value in separating **“things I want to render”** from **“plumbing to make it happen.”**

---

# 📌 Big Picture
- Learned the **full Metal pipeline**: vertex → rasterizer → fragment → framebuffer.  
- Understood how **shaders** act as small programs while Swift orchestrates state.  
- Realized every API “strictness” reflects deeper principles:  
  - Clip-space math.  
  - GPU architecture.  
  - Language-level initialization rules.  

---

# 🔮 Next Steps
- [[Textures in Metal]] — load and sample images in shaders.  
- [[Uniform Buffers]] — pass transformation matrices and parameters to shaders.  
- [[3D Transformations]] — model, view, projection matrices in Metal.  
- [[Lighting in Shaders]] — diffuse, specular, normal-based shading.  
- [[Compute Shaders in Metal]] — go beyond graphics into general GPU work.  