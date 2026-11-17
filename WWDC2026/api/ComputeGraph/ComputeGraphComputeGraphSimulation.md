- ComputeGraph  
- ComputeGraphSimulation  
  
Class  
  
# ComputeGraphSimulation  
  
A simulation of particles, which use a single pipeline.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ tvOS 27.0+ visionOS 27.0+ Reality Composer Pro  
  
``` swift  
final class ComputeGraphSimulation  
```  
  
## Overview  
  
This class is independent of the output, which makes for simpler testing.  
  
## Topics  
  
### Structures  
  
struct AdvanceParams  
  
Parameters for advancing a compute graph simulation by one time step.  
  
struct SimulationRate  
  
Specifies the rate and mode for simulation.  
  
### Initializers  
  
convenience init(pipelines: ComputeNodeGraph.Pipelines?)  
  
Initialize a ComputeGraphSimulation for the given pipelines, or a default pipeline if not specified.  
  
convenience init(pipelines: ComputeNodeGraph.Pipelines, commandQueue: any MTLCommandQueue)  
  
Initialize a ComputeGraphSimulation for the given pipelines  
  
### Instance Properties  
  
var commandQueue: any MTLCommandQueue  
  
var graphUniforms: any MTLBuffer  
  
Returns a read-only copy of the uniforms buffer.  
  
var pipelines: ComputeNodeGraph.Pipelines  
  
var simulationRate: ComputeGraphSimulation.SimulationRate  
  
Specifies the current simulation rate.  
  
### Instance Methods  
  
func addUserResource(any MTLResource)  
  
Registers a resource for residency on all command encoders used by this simulation.  
  
func advance(ComputeGraphSimulation.AdvanceParams)  
  
Advances the simulation by one time step, encoding all simulation stage dispatches into the command buffer and encoder provided by params.  
  
func buffer(at: Int) -> (any MTLBuffer, bufferOffset: Int)?  
  
func fastForward()  
  
func fastForward(stepCount: Int, stepDeltaTime: Float)  
  
Advances the particle simulation by multiple steps in a single operation.  
  
func isOutputEnabled(Int) -> Bool  
  
Returns whether the specified output is currently enabled for simulation.  
  
func modifyUniforms<E, R>((UnsafeMutableRawBufferPointer) throws(E) -> R) throws(E) -> R  
  
Provides read/write access to the entire uniforms buffer for CPU access.  
  
func reset(encoder: any MTLComputeCommandEncoder)  
  
Resets the simulation to its initial state, clearing all live elements and accumulated time.  
  
func resetRandomSeeds(using: () -> UInt32)  
  
Resets random seeds using the provided randomness function.  
  
func setBuffer((any MTLBuffer)?, bufferOffset: Int, at: ComputeNodeGraph.Assembly.Location)  
  
func setBuffer((any MTLBuffer)?, bufferOffset: Int, at: Int)  
  
func setBuffer(any MTLBuffer, bufferOffset: Int, elementCount: Int, at: ComputeNodeGraph.Assembly.Location)  
  
func setBuffers([(any MTLBuffer)?], bufferOffsets: [Int]?)  
  
func setOutputEnabled(Int, enabled: Bool)  
  
Enables or disables execution of the provided output stage, without disabling the system it represents.  
  
func setTexture((any MTLTexture)?, at: Int)  
  
Binds a Metal texture to the texture slot at the given index.  
  
func setTextures([(any MTLTexture)?])  
  
func setUniform<V>(V, named: String) -> Bool  
  
Finds the named uniform and sets it to the given BitwiseCopyable value.  
  
func setUniformData(Data, at: ComputeNodeGraph.Assembly.Location)  
  
func setUniformValue<V>(V, at: ComputeNodeGraph.Assembly.Location)  
  
Copies the contents of value into the location specified by relocation.  
  
func setUserResources([any MTLResource])  
  
Sets additional resources for residency on all command buffers used by this simulation, replacing any previously added resources.  
  
func spawn(elements: borrowing [ElementSpawnParameters], in: Int?, using: any MTLComputeCommandEncoder)  
  
Spawns new elements into the simulation with the given initial parameters.  
  
func texture(at: Int) -> (any MTLTexture)?  
