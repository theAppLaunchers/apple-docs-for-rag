

- Model I/O
- MDLVoxelArray
-  init(asset:divisions:interiorShells:exteriorShells:patchRadius:) Deprecated

Initializer

# init(asset:divisions:interiorShells:exteriorShells:patchRadius:)

Initializes a voxel array that models the volume of 3D objects in the specified asset and creates the specified number of voxel shells.

macOS 10.11–10.12Deprecated

``` source
init(
    asset: MDLAsset,
    divisions: Int32,
    interiorShells: Int32,
    exteriorShells: Int32,
    patchRadius: Float
)
```

## Parameters 

`asset`  

An asset containing meshes whose volume is to be modeled as voxels.

`divisions`  

The number of divisions to create along the y-axis of the asset’s bounding box; that is, the height in voxels of the resulting voxel array.

`interiorShells`  

The number of concentric shells of voxels to generate inside the object’s surface.

`exteriorShells`  

The number of concentric shells of voxels to generate outside the object’s surface.

`patchRadius`  

The largest radius, in world space units, of patches to apply to create closed volumes from meshes in the asset.

## Return Value

A new voxel array.

## Discussion

When you create a voxel array from an asset, Model I/O analyzes any meshes contained in the asset to determine the volume of the 3D objects modeled by those meshes. This initializer discretizes that volume by dividing the asset’s boundingBox coordinates into a three-dimensional grid. The `divisions` parameter determines the height of the grid in voxels. Because single voxel is a cubic unit, the width and depth of the grid in voxels is proportional to its height and the bounding box of the asset.

After dividing the bounding box into a grid, Model I/O generates a shell of voxels at the grid positions corresponding to points on the mesh’s surface. Each voxel is a MDLVoxelIndex value whose x, y, and z coordinates locate the voxel in the grid and whose w coordinate value is 0, indicating that the voxel is on the surface of the object.

If you pass a value greater than zero for the `interiorShells` or `exteriorShells` parameter, this initializer also generates voxel data for the grid positions within or outside of the surface. For example, if you pass an `interiorShells` value of `1`, Model I/O generates a single concentric shell of voxels inside the surface. For those voxels, the w coordinate indicates how many shells lie between that voxel and the surface shell.

## See Also

### Creating a Voxel Array

init(asset: MDLAsset, divisions: Int32, interiorNBWidth: Float, exteriorNBWidth: Float, patchRadius: Float)

Initializes a voxel array that models the volume of 3D objects in the specified asset, creating voxel shells for the specified distances from the object’s surface.

Deprecated

init(data: Data, boundingBox: MDLAxisAlignedBoundingBox, voxelExtent: Float)

Initializes a voxel array with the specified voxel data.

