*   [PhotosUI](/documentation/photosui)
*   PhotosPicker

Structure

# PhotosPicker

A view that displays a Photos picker for choosing assets from the photo library.

PhotosUISwiftUIiOS 16.0+iPadOS 16.0+Mac CatalystmacOS 13.0+visionOSwatchOS 9.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor) @preconcurrency
struct PhotosPicker<Label> where Label : [`View`](/documentation/SwiftUI/View)
```

```
```
```
```
```
```
```

## [Overview](/documentation/PhotosUI/PhotosPicker#overview)

Use the Photos picker view to browse and select images and vidoes from the photo library. The view contains methods for single selection and multiple selection. For example, the following code displays a button that — when pressed — shows a picker in multiple selection mode.

```swift

```swift
import SwiftUI
import PhotosUI
```swift
```swift
struct PhotosSelector: View {
```
```
    @State var selectedItems: [PhotosPickerItem] = []
    var body: some View {
        PhotosPicker(selection: $selectedItems,
                     matching: .images) {
            Text("Select Multiple Photos")
        }
    }
}
```

```

When displaying the picker, you can use [`PHPickerFilter`](/documentation/photosui/phpickerfilter-swift.struct) options to customize what it displays. For example, the following code displays [`images`](/documentation/photosui/phpickerfilter-swift.struct/images) and excludes [`screenshots`](/documentation/photosui/phpickerfilter-swift.struct/screenshots).

```

```
PhotosPicker(selection: $selectedItems,
             matching: .any(of: [.images, .not(.screenshots)])) {
    Text("Select Photos")
}
```

```

The selection results you get are placeholder objects. A [`PhotosPickerItem`](/documentation/photosui/photospickeritem) conforms to [`Transferable`](/documentation/CoreTransferable/Transferable), and allows you to load a representation you request. To load a SwiftUI [`Image`](/documentation/SwiftUI/Image) and track progress, use [`loadTransferable(type:completionHandler:)`](/documentation/photosui/photospickeritem/loadtransferable\(type:completionhandler:\)).

```swift
```swift
```swift
```swift
```swift
```swift
func loadTransferable(from imageSelection: PhotosPickerItem) -> Progress {
```
```
    return imageSelection.loadTransferable(type: Image.self) { result in
        DispatchQueue.main.async {
            guard imageSelection == self.imageSelection else { return }
            switch result {
            case .success(let image?):
                // Handle the success case with the image.
            case .success(nil):
                // Handle the success case with an empty value.
            case .failure(let error):
                // Handle the failure case with the provided error.
            }
        }
    }
}
```
```
```
```

A failure can occur when the system attempts to retrieve the data. For example, if the picker tries to download data from iCloud Photos without a network connection.

Important

[`Image`](/documentation/SwiftUI/Image) only supports `PNG` file types through its [`Transferable`](/documentation/CoreTransferable/Transferable) conformance, so you need to create a custom `Transferable` model to support other image types. See [Bringing Photos picker to your SwiftUI app](/documentation/photokit/bringing-photos-picker-to-your-swiftui-app) to learn more.

## [Topics](/documentation/PhotosUI/PhotosPicker#topics)

### [Creating a picker](/documentation/PhotosUI/PhotosPicker#Creating-a-picker)

[`init(selection: Binding<PhotosPickerItem?>, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy, label: () -> Label)`](/documentation/photosui/photospicker/init\(selection:matching:preferreditemencoding:label:\))

Creates a picker that selects an item and optionally configures the types of items to show, item encoding, and label behavior.

[`init(selection: Binding<[PhotosPickerItem]>, maxSelectionCount: Int?, selectionBehavior: PhotosPickerSelectionBehavior, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy, label: () -> Label)`](/documentation/photosui/photospicker/init\(selection:maxselectioncount:selectionbehavior:matching:preferreditemencoding:label:\))

Creates a picker that selects a collection of items and optionally configures the max selection count, selection behavior, types of items to show, item encoding, and label behavior.

[`init(selection: Binding<PhotosPickerItem?>, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy, photoLibrary: PHPhotoLibrary, label: () -> Label)`](/documentation/photosui/photospicker/init\(selection:matching:preferreditemencoding:photolibrary:label:\))

Creates a picker that selects an item from the photo library you specify and optionally configures the types of items to show, item encoding, and label behavior.

[`init(selection: Binding<[PhotosPickerItem]>, maxSelectionCount: Int?, selectionBehavior: PhotosPickerSelectionBehavior, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy, photoLibrary: PHPhotoLibrary, label: () -> Label)`](/documentation/photosui/photospicker/init\(selection:maxselectioncount:selectionbehavior:matching:preferreditemencoding:photolibrary:label:\))

Creates a picker that selects a collection of items from the photo library you specify and optionally configures the max selection count, selection behavior, types of items to show, item encoding, and label behavior.

### [Creating a picker with a title](/documentation/PhotosUI/PhotosPicker#Creating-a-picker-with-a-title)

[`init(LocalizedStringKey, selection: Binding<PhotosPickerItem?>, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy)`](/documentation/photosui/photospicker/init\(_:selection:matching:preferreditemencoding:\)-7jbef)

Creates a picker with a title key and selection, and optionally configures the types of items to show and item encoding behavior.

[`init<S>(S, selection: Binding<PhotosPickerItem?>, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy)`](/documentation/photosui/photospicker/init\(_:selection:matching:preferreditemencoding:\)-48f7l)

Creates a picker with a title and selection, and optionally configures the types of items to show and item encoding behavior.

[`init(LocalizedStringKey, selection: Binding<[PhotosPickerItem]>, maxSelectionCount: Int?, selectionBehavior: PhotosPickerSelectionBehavior, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy)`](/documentation/photosui/photospicker/init\(_:selection:maxselectioncount:selectionbehavior:matching:preferreditemencoding:\)-8ac23)

Creates a picker with a title key and selection, and optionally configures the max selection count, selection behavior, types of items to show, item encoding, and label behavior.

[`init<S>(S, selection: Binding<[PhotosPickerItem]>, maxSelectionCount: Int?, selectionBehavior: PhotosPickerSelectionBehavior, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy)`](/documentation/photosui/photospicker/init\(_:selection:maxselectioncount:selectionbehavior:matching:preferreditemencoding:\)-6m11r)

Creates a picker with a title and selection, and optionally configures the max selection count, selection behavior, types of items to show, item encoding, and label behavior.

[`init(LocalizedStringKey, selection: Binding<PhotosPickerItem?>, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy, photoLibrary: PHPhotoLibrary)`](/documentation/photosui/photospicker/init\(_:selection:matching:preferreditemencoding:photolibrary:\)-bu7c)

Creates a picker with a title key and selection from the photo library you specify, and optionally configures the types of items to show, item encoding, and label behavior.

[`init<S>(S, selection: Binding<PhotosPickerItem?>, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy, photoLibrary: PHPhotoLibrary)`](/documentation/photosui/photospicker/init\(_:selection:matching:preferreditemencoding:photolibrary:\)-6bm2n)

Creates a picker with a title and selection from the photo library you specify, and optionally configures the types of items to show, item encoding, and label behavior.

[`init(LocalizedStringKey, selection: Binding<[PhotosPickerItem]>, maxSelectionCount: Int?, selectionBehavior: PhotosPickerSelectionBehavior, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy, photoLibrary: PHPhotoLibrary)`](/documentation/photosui/photospicker/init\(_:selection:maxselectioncount:selectionbehavior:matching:preferreditemencoding:photolibrary:\)-5tpfd)

Creates a picker with a title key and selection from the photo library you specify, and optionally configures the max selection count, selection behavior, types of items to show, item encoding, and label behavior.

[`init<S>(S, selection: Binding<[PhotosPickerItem]>, maxSelectionCount: Int?, selectionBehavior: PhotosPickerSelectionBehavior, matching: PHPickerFilter?, preferredItemEncoding: PhotosPickerItem.EncodingDisambiguationPolicy, photoLibrary: PHPhotoLibrary)`](/documentation/photosui/photospicker/init\(_:selection:maxselectioncount:selectionbehavior:matching:preferreditemencoding:photolibrary:\)-6fwsc)

Creates a picker with a title and selection from the photo library you specify, and optionally configures the max selection count, selection behavior, types of items to show, item encoding, and label behavior.

## [Relationships](/documentation/PhotosUI/PhotosPicker#relationships)

### [Conforms To](/documentation/PhotosUI/PhotosPicker#conforms-to)

*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`View`](/documentation/SwiftUI/View)

## [See Also](/documentation/PhotosUI/PhotosPicker#see-also)

### [Photos picker for SwiftUI](/documentation/PhotosUI/PhotosPicker#Photos-picker-for-SwiftUI)

[

Bringing Photos picker to your SwiftUI app](/documentation/photokit/bringing-photos-picker-to-your-swiftui-app)

Select media assets by using a Photos picker view that SwiftUI provides.

[

Implementing an inline Photos picker](/documentation/photokit/implementing-an-inline-photos-picker)

Embed a system-provided, half-height Photos picker into your app’s view.

```swift
```swift
```swift
struct PhotosPickerItem
```
```

A type that represents an item you use with a Photos picker.
```
```swift
```swift
```swift
struct PhotosPickerSelectionBehavior
```
```

A type that describes how the Photos picker handles user selection.
```
```swift
```swift
```swift
struct PhotosPickerStyle
```
```
```