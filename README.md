# An obj renderer with OpenGL
The name might be TeapotVisualStudio, but it can render .obj files!

Usage:
  TeapotVisualStudio.exe <filename.obj>
  the .obj file should contain a material that also includes ambient, diffuse, and specular maps
  Paths to the maps should be relative to the .obj file

# Configuring Visual Studio
1. Create a new visual studio empty C++ project, then add all of the files to the
   solution folder
2. Set the target platform to x86
3. Do not forget to do step 2
2. Add main.cpp to Source Files in Visual Studio
3. Add lodepng.cpp to source files in Visual Studio from
   include -> lodepng -> lodepng.cpp
4. Open the TeaponSolution Project properties
5. Go to C/C++, then add the following Additional Include Directories. 
   $\$$(SolutionDir)include
   $\$$(SolutionDir)include\freeglut\include\
   $\$$(SolutionDir)include\glew\include\
6. Go to Linker -> General, and ad the following to Additional Library Directories
   $\$$(SolutionDir)include\freeglut\lib\$\$$(LibrariesArchitecture)\
   $\$$(SolutionDir)include\glew\lib\Release\$\$$(LibrariesArchitecture)\
7. Then under Linker -> Input, add the following to Additional Dependencies
   freeglut.lib
   glew32.lib

# Descirption
This is an OpenGL program that loads a teapot object and displays it on the screen.
This program demonstrates:
  - Converting an obj file to a format that can be used with OpenGL
  - Processing vertex, normal, and texture data to be used in an element buffer
  - Blinn Phong shading with ambient, diffuse, and specular lighting
  - A camera that can be rotated around the object
  - A light that can be rotated around the object

# Functionality
Keyboard functionality:
  - a: Toggle ambient lighting
  - s: Toggle specular lighting
  - d: Toggle diffuse lighting
  - F6: Recompile shaders
  - ESC: Close the window
  - Arrow keys: Rotate the light

Mouse functionality:
  - Left click and drag: Rotate the camera
  - Scroll wheel: Zoom in and out

# Discussion
Notes: 
	I created this project trying to follow the structure of cyCodeBase. 
	All of the files in rcCodeBase are .h files, and I am not entirely 
	pleased with this. 
	After starting the projects and examples from Donald H. House's Physics
	Based Animation course,	I got an example of what a clean C++ project 
	looks like. If I were to redo this project, I would	more strictly adhere
	to the single responsibility principle and separate the classes into .h
	and .cpp files.	Having the files split more strictly into a Model-View-Controller
	structure would have also greatly benifited this project.
