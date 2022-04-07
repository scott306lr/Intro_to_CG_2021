CG_Final

#### Pipeline
![](https://i.imgur.com/TgdsrLC.png) 

#### Breham's Algorithm
![](https://i.imgur.com/lE6X0Ow.png) 

#### Area Sampling (Prefiltering)



## Ch.8 Hidden Surface Removal & Culling

### Back-face Removal (Culling)
Visible only if cos >= 0 or dot(v, n) >= 0
* solved self-occlusion
* don't work on nonconvex objects

### Hidden Surface Removal

#### Painter's Algorithm
Render polygons in a back to front order
* there will be a problem when two objects overlap one another

#### Depth Sort
O(nlogn) for ordering
Deal with the easy cases, then the hard ones
* easy cases
    * behind all other polygons
    * overlap in z, but not in x and y
* difficult cases
    * cylclic overlap
    * penetration

#### Z-Buffer / Depth-Buffer Algorithm

* z/depth buffer
    * stores the depth of the closest object at each pixel found so far
* as we render each polygon, compare the depth of each pixel to depth in z buffer
    * if less, place the shade of pixel in the color buffer and update z buffer
* depth change satisfy $a\Delta x+b\Delta y+c\Delta z=0$
    * along scan line $\Delta y=0$ , then $\Delta z= \frac{-a}{c}\Delta x$
    * in screen space, $\Delta x=1$

### Interpolation of Z values
* Interpolate after perspective projection transformation to get correct color.
#### Octree
![](https://i.imgur.com/O8zHB7e.png) 

#### BSP Tree (Binary Space Partitioning Tree)
![](https://i.imgur.com/51Q2crZ.png) 
![](https://i.imgur.com/UlAyLv9.png) 

## Ch.9 Buffers and Mapping Techniques
### Mapping Methods
* Texture Mapping
    * Backward Mapping
    * Two-part Mapping: Cylindrical, Spherical, Box Mapping
    * Second Mapping
    * Mipmap (prefiltering method)
    ![](https://i.imgur.com/OzP7ngc.png) 
* Environment Mapping
    * Lattitude, Sphere, Cube Mapping
* Normal and Bump Mapping
    * bump map shows height, normal map can be more detailed(angle...)
    * both needs Phong Shading to work

![](https://i.imgur.com/WnGcOgS.png) 

### Anti-aliasing

#### Post Filtering
* FSAA (Full screen) / SSAA (Supersample)
    * 1024 * 1024 -> 4096 * 4096 
* MSAA (Multiple samples)
    * uses larger buffer to calculate subsample coverage, averages the color
* DLSS (Deep learning super sampling)
    * low-res current frame + high-res previous frame to generate current frame with a higher quality
* CSAA-NVIDIA and CFAA-AMD
#### Prefiltering
* Area sampling
#### Pixel phasing
pixel positions are shifted to nearly approximate positions near object geometry
![](https://i.imgur.com/woddvvH.jpg) 

#### Shader Code
vertex shader
![](https://i.imgur.com/EyMfBeD.png) 

geometry shader (pass var)
![](https://i.imgur.com/1ESVNwS.png) 

fragment shader
![](https://i.imgur.com/hS8fRRf.png) 

