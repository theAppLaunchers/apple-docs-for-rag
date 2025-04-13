

- RoomPlan
-  Providing custom models for captured rooms and structure exports 

Sample Code

# Providing custom models for captured rooms and structure exports

Enhance the look of an exported 3D model by substituting object bounding boxes with detailed 3D renditions.

Download

iOS 17.0+iPadOS 17.0+Mac Catalyst 18.2+Xcode 16.2+

## Overview

Note

This sample code project is associated with WWDC23 session 10192: Explore enhancements to RoomPlan.

### Configure the sample code project

Before you run the `RoomPlanExporter` target in Xcode:

1.  Set the run destination to an iOS 17 or later device; this app doesn’t support Simulator.

2.  Export a scanned room in JSON format, which you generate with the RoomCaptureView sample app. Alternatively, you can generate a JSON export of several rooms merged into a single structure by using the Scan-merging sample app.

To run the app:

1.  Run the `RoomPlanExporter` target.

2.  Tap Open a CapturedRoom and choose a scanned room or structure in JSON format in the Open File dialog.

3.  Tap Export and choose the Model option.

4.  Tap Share Export and observe the output files in the resulting `Export` folder. The USDZ output file features a detailed 3D model in replacement for any object in the room that the framework recognizes during the scan as being one of the known object types from the target’s `RoomPlanCatalog.bundle`.

The `RoomPlanCatalogGenerator` target in Xcode provides a command-line tool that enables you to generate your own catalog of 3D models similar to the `RoomPlanCatalog.bundle` in this sample code project. Before running the tool, set the run destination to a macOS 14 or later device with Mac Catalyst, and enable the command-line argument as follows:

1.  Select the `RoomPlanCatalogGenerator` scheme and choose Edit Scheme.

2.  Select the Run task’s Arguments tab.

3.  Click or tap the checkbox to enable just the first argument:

```
create-folders -i "~/RoomPlan/Catalog/"
```

4.  Run the scheme in Xcode, which creates a folder structure at the `~/RoomPlan/Catalog` location on disk.

5.  Fill the folder structure with 3D models that correspond to the folder names. The folder names correspond to the types of objects and attributes that RoomPlan recognizes during a scan. The framework supports 3D models in `.usdc` format (preferred), and `.abc`, `.obj`, `.ply`, or `.stl` formats.

6.  If you don’t have your own 3D models, you can use the 3D models that this sample code project provides by substituting the `~/RoomPlan/Catalog/Resources` folder on disk for the sample code project’s `/RoomPlanExporter/RoomPlanCatalog.bundle/Resources` folder.

7.  Select the `RoomPlanCatalogGenerator` scheme and choose ‘Edit Scheme’.

8.  In the Run task’s Arguments pane, click or tap the checkbox to enable just the second argument:

```
generate -i "~/RoomPlan/Catalog" \
         -o "~/RoomPlan/RoomPlanCatalog.bundle"
```

9.  Run the scheme in Xcode, which generates a `RoomPlanCatalog.bundle` file from the folder structure filled with 3D models.

10. Place a scanned room in JSON format at the `~/RoomPlan/Room.json` path on disk. You generate the file by exporting a scanned room with the RoomCaptureView sample app, or by exporting several rooms merged into a single structure with the Scan-merging sample app.

11. Select the `RoomPlanCatalogGenerator` scheme and choose ‘Edit Scheme’.

12. In the Run task’s Arguments pane, click or tap the checkbox to enable just the third argument:

```
convert -i "~/RoomPlan/Room.json" \
        -c "~/RoomPlan/RoomPlanCatalog.bundle" \ 
        -o "~/RoomPlan/Room.usdz"
```

13. Run the scheme in Xcode, which converts the serialized room or structure to a USDZ file at path `~/RoomPlan/Room.usdz` on disk that includes substituted 3D models from the catalog bundle.

## See Also

### 3D Asset Output

class RoomBuilder

An object that generates a 3D asset from room-capture data.

class StructureBuilder

An object that combines multiple scan sessions into a single captured result.

struct USDExportOptions

Options that determine the underlying data format of a scan export.

