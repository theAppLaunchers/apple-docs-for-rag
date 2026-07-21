ComputeGraph  
  
- ComputeGraph  
-  Compute Graph  
  
Framework  
  
# Compute Graph  
  
Build and run custom particle effects and compute simulations for RealityKit using a programmable node graph.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ tvOS 27.0+ visionOS 27.0+ Reality Composer Pro  
  
## Overview  
  
Compute Graph is a node-based framework for constructing particle simulations and general-purpose GPU compute graphs in RealityKit. Whereas ShaderGraph lets developers build material appearance through a node-based visual editor, Compute Graph provides the same graph-driven, connection-based authoring for simulation behavior. The technology targets tool and editor developers who need fine-grained, per-stage control over how particles and compute work proceeds.  
  
The Swift API centers on a three-step compilation pipeline. Describe a simulation as a GraphDefinition, a directed graph of typed nodes and edges. Then assemble the graph into a ComputeGraphAssembly, which resolves the buffer, uniform, and texture layout the simulation requires. Compile that assembly into ComputeGraphPipelines to produce GPU shader code; a single set of pipelines can back multiple ComputeGraphSimulation instances running concurrently. Library and SyntheticNodeLibrary let you supply custom Metal Shading Language functions as node definitions alongside the framework’s built-in set in ComputeGraphBuiltIns.  
  
At runtime, ComputeGraphSimulation drives GPU execution. Call advance(_:) each frame, passing an ComputeGraphSimulation.AdvanceParams that carries the time delta, a Metal command buffer, a compute encoder, and optional world-space transforms. Bind GraphBuffer, GraphTexture, and GraphUniform resources before the first advance. To inject elements programmatically, call spawn(elements:in:using:) with ElementSpawnParameters values that set each element’s initial position, velocity, size, color, and lifetime.  
  
## Topics  
  
### Simulation objects  
  
class ComputeGraphSimulation  
  
A simulation of particles, which use a single pipeline.  
  
### Built-in nodes  
  
element  
  
A set of nodes for reading and writing the current element within a particle simulation.  
  
emitter  
  
A set of nodes usable in the emission stage of a simulation, which control how often and how many elements to spawn.  
  
force  
  
Apply physics forces including gravity, drag, noise, and twist.  
  
initialize  
  
Nodes usable within the initialization stage of an element.  
  
output  
  
Nodes usable within the output stage of an element. You can use these nodes to change the appearance of an element without making modifications to the element itself.  
  
module  
  
Mutate per-particle state with operations such as setPosition, addPosition, setVelocity, setColor, setSize, and setLifetime.  
  
graph  
  
A set of nodes usable in any stage within a ComputeGraph.  
  
group  
  
Nodes for querying the group for a current particle. Requires a system whose simulation stage is configured as either strips or grouped.  
  
texture  
  
Nodes usable within the texture stage, for generating textures.  
  
random  
  
Nodes for generating pseudo-random numbers.  
  
matrix4x4f  
  
Transform positions and directions using matrix4x4f.  
  
matrix4x4h  
  
Transform positions and directions using matrix4x4h.  
  
### Node parameters and connections  
  
struct PortReference  
  
A reference to another group’s values.  
  
enum BinaryOperation  
  
An enumeration of binary operations.  
  
enum UnaryOperation  
  
An enumeration of single-operand operations.  
  
enum StandardLibraryFunction  
  
### Elements and particles  
  
enum ElementGrouping  
  
An enumeration of how elements are grouped.  
  
struct ElementSpawnParameters  
  
Parameters used to configure the initial state of a particle when it’s spawned in the simulation.  
  
enum Sorting  
  
An enumeration of sorting modes.  
  
### Graph resources  
  
enum AddressSpace  
  
A GPU memory address space.  
  
### Geometry and simulation inputs  
  
enum CoordinateSpace  
  
Simulation coordinate space, controlling how positions and orientations are stored.  
  
enum StripOrientation  
  
An enumeration that specifies how a strip should be oriented.  
  
struct Viewpoint  
  
Camera viewpoint parameters in 3D space.  
  
struct MouseParams  
  
Parameters describing mouse interaction in 3D space.  
  
### Structures  
  
struct ComputeNodeGraph  
  
### Functions  
  
void element_integrate()  
  
void filteredLinesFromNeighbors(grid, positions, groupings, outputSegments, maxDistance)  
  
void gridDebugCells(grid)  
  
void gridFromPoints(gridStorage, inputPositions, inputFlags)  
  
void linesFromNeighbors(grid, positions, outputSegments, maxDistance)  
  
void orient_to_velocity()  
  
Orient the particle by setting its axisY to the velocity’s current direction.  
  
void spawn_demo()  
  
float4 texture_sample(texture, uv)  
  
float4 texture_sample1d(texture, u)  
  
Viewpoint viewpoint()  
  
Returns the current viewpoint, if one is provided.  
