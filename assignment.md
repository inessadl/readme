# mesh-simplification

This repository contains the first assignment of Computer Graphics class from the Computer Science course of Federal University of Pelotas (UFPel), Brazil.


## Description

Implement a simple mesh simplification using:

- priority queue
- vertex removal

## Building on Linux

I have used Ubuntu 14.04 for the project. For other versions the instructions should be similar (check [OpenGL Tutorial](http://www.opengl-tutorial.org/) for other distributions or operating systems).

### Dependencies

- Install the latest drivers
- Install all needed compilers, tools & libs:

``` $ sudo apt-get install cmake make g++ libx11-dev libxi-dev libgl1-mesa-dev libglu1-mesa-dev libxrandr-dev libxext-dev libxi-dev ```

### Building

After clone or download (and unzip) the repository go to the root and type:

```
$ cd Assignment-01/external/glfw-3.0.3
$ cmake .
$ make all
$ cd ../..
$ mkdir build
$ cd build
$ cmake ..
$ make all
```

I've used CLion IDE for running and debugging, so the execution could be done using the graphical interface of the IDE.


## Mesh Simplification



### 1. Priority Queue

The heuristic defined for vertex removal is described on pseudo-code as follows:

- Go through all the vertex and calculate their connection with others (edges)
- Store the edges on a 2D vector together with the 'index' of its vertex
- Sort the vector by the size of the edges (smallest first)
- Get the first position of the vector which contains the two vertex to be compared
- Verify which of the two vertex has more connections (v1) and choose to be removed


### 2. Half-Edge Collapse

The technique chosen for vertex removal was the *Half-Edge Collapse* which works removing a vertex and reconnecting all its connections to another vertex:


![Half-Edge Collapse](http://jcae.sourceforge.net/amibe-doc/org/jcae/mesh/amibe/ds/doc-files/AbstractHalfEdge-2.png)


Pseudo-code:

- Go to the vertex to be removed (v1 - defined on priority queue)
- Check all the vertex that are connected to that vertex
- Remove v1 and reconnect all its connections to v2  


## References


David Luebke, Benjamin Watson, Jonathan D. Cohen, Martin Reddy, and Amitabh Varshney. 2002. *Level of Detail for 3D Graphics*. Elsevier Science Inc., New York, NY, USA.

OpenGL Tutorials. *Tutorial 1: Opening a Window*, Available at: http://www.opengl-tutorial.org/beginners-tutorials/tutorial-1-opening-a-window/ (Accessed: 3rd April 2016).

Mesh Simplification. Standford course (CS 468-10-fall) Lecture Notes. Available on: http://graphics.stanford.edu/courses/cs468-10-fall/LectureSlides/08_Simplification.pdf

Shene, Ching-Kuang. *Mesh Simplification*. Classes notes. Michigan Technological University. Available on:
http://www.cs.mtu.edu/~shene/COURSES/cs3621/SLIDES/Simplification.pdf
