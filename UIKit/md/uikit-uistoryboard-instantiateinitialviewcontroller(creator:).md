

- UIKit
- UIStoryboard
-  instantiateInitialViewController(creator:) 

Instance Method

# instantiateInitialViewController(creator:)

Creates the initial view controller from the storyboard and initializes it using your custom initialization code.

iOS 13.0+iPadOS 13.0+Mac CatalysttvOS 13.0+visionOS

``` source
@MainActor @preconcurrency
func instantiateInitialViewController(creator: ((NSCoder) -> ViewController?)? = nil) -> ViewController? where ViewController : UIViewController
```

## Parameters 

`creator`  

A block containing your custom creation code for the view controller. Use this block to create the view controller, initialize it with the provided `coder` object and any custom information you require, and return the result. This block returns a new view controller object and takes the following parameter:

coder  
The coder object containing the storyboard data to use when configuring the view controller.

If you return `nil` from your block, this method creates the view controller using the default init(coder:) method.

## Return Value

The initial view controller in the storyboard.

## Mentioned in 

Displaying and managing views with a view controller

## Discussion

Every storyboard file has an initial view controller that represents the default view controller to create. Typically, you use the initial view controller as the root view controller for a window. However, you can also instantiate the initial view controller when transitioning to content in a new storyboard file.

This method creates a new instance of the initial view controller using the custom block you provide. In your block, create the view controller using your custom initialization method and return it. Your custom initialization method must accept an NSCoder parameter and must call the inherited init(coder:) method at some point during its execution. Not doing so is a programmer error.

## See Also

### Loading the Initial View Controller

func instantiateInitialViewController() -> UIViewController?

Creates the initial view controller and initializes it with the data from the storyboard.

