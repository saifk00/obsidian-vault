[GitHub repo](https://github.com/saifk00/render-system)
![[Pasted image 20231117184512.png]]
![[Pasted image 20231117184525.png]]
Above are some images rendered with OpenGL in C++. Assimp was used to load the backpack model, and GLFW was the windowing system. One of many things I was able to do by following along with [this wonderful series](https://learnopengl.com/) (the first image in particular is the result of completing the [Model Loading](https://learnopengl.com/Model-Loading/Model) section). Essentially, we use Assimp to load the object into memory, convert it into a series of meshes, textures, and lighting maps (in this case just diffuse and spectral), then load the former into openGL using vertex buffer objects bound to VAOs. Once the VAOs are set up we can draw by iterating over the model's meshes, binding the appropriate VAOs and textures, and thus render the image. The shaders are fairly simple, loading the vertices, element indices, normals, and texture coordinates according to the VAO, and using the phong lighting model to calculate the colors: ambient, diffuse (along with an inverse quadratic attenuation factor), and specular. Some mistakes I made (and learned from) in no particular order:

- Unbinding the VAO _after_ unbinding the VBOs/Element Buffers (VAO sets its VBO as the last one that was bound, unbinding the VBO sets this to 0)
- When transforming an object and using the phong model, forgetting to transform the normal vectors accordingly (e.g. for a rotation of the object, we also need to rotate `vec4(Normal, 0.0)` where the quaternion's scalar value is 0 since it is a direction)
- Forgetting to `glEnableVertexAttribArray()` for a particular index, or, similarly, forgetting to `glBindTexture()`

Below is an animation created in the program demonstrating the texture loading, lighting effects, and various transformations (e.g. using quaternions to rotate the light):
![[bag_eye_anim.ef0890b8.webm]]
In the interest of letting other people test it out, I also had to brush up on CMake and refactor my project (which was initially created in visual studio) to use it. Getting it to play well with external libraries was a chore but I managed to get it working, and can confirm the build works out of the box on Windows and Linux. I've also included some binaries under releases.