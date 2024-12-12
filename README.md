# An obj renderer with OpenGL

For a more in depth breakdown of the code, checkout the [blog breakdown](https://www.richardcato.com/blogs/interactivecomputergraphics)

Usage:
  TeapotVisualStudio.exe <path_to.obj>
  the .obj file should contain a material that also includes ambient, diffuse, and specular maps
  Paths to the maps should be relative to the .obj file

# Running the code
1. OpenTeapotVisualStudio.sln, the visual studio solution
2. Set the platform to x86 and the build mode to release
3. Build the solution
4. Navigate to the Release folder
5. Confirm that ObjRenderer.exe is in the Release folder along with
    1. brick.png
    2. brick-specular.png
    3. freeglut.dll
    4. shader.frag
    5. shader.vert
    6. teapot.mtl
    7. teapot.obj
6. You can now run ObjRenderer.exe from the command prompt with ObjRendere.exe <path_to.obj>

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
    1. \$(SolutionDir)include
    2. \$(SolutionDir)include\freeglut\include\ 
    3. $(SolutionDir)include\glew\include\ 
6. Go to Linker -> General, and ad the following to Additional Library Directories 
    1. $(SolutionDir)include\freeglut\lib\\$(LibrariesArchitecture)\ 
    2. $(SolutionDir)include\glew\lib\Release\\$(LibrariesArchitecture)\ 
7. Then under Linker -> Input, add the following to Additional Dependencies
    1. freeglut.lib
    2. glew32.lib
8. Under Build Events, add the following to Post-Build Event Command Line.
    1. copy /Y "$(SolutionDir)brick.png" "$(TargetDir)"
    1. copy /Y "$(SolutionDir)brick-specular.png" "$(TargetDir)"
    1. copy /Y "$(SolutionDir)shader.vert" "$(TargetDir)"
    1. copy /Y "$(SolutionDir)shader.frag" "$(TargetDir)"
    1. copy /Y "$(SolutionDir)teapot.mtl" "$(TargetDir)"
    1. copy /Y "$(SolutionDir)teapot.obj" "$(TargetDir)"
9. You can now build, then launch ObjRenderer.exe from the command prompt in the Release folder. 


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
