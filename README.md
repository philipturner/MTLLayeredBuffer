# MTLLayeredBuffer

A package encapsulating `MTLLayeredBuffer` from ARHeadsetKit. This type is not included in ARHeadsetUtil since it is distinct from the other utilities. For more about it, refer to [its article](https://github.com/philipturner/ARHeadsetKit/blob/main/docs/articles/layered-buffer.md) in the ARHeadsetKit [article series](https://github.com/philipturner/ARHeadsetKit/blob/main/docs/article-list.md).

> NOTE to self: switch the dependency from ARHeadsetUtil/temp to ARHeadsetUtil/main after validating that it works correctly

Due to problems with Swift's naming system, this module cannot have the same name as a type it encapsulates. This is the reason why [Swift Numerics](https://github.com/apple/swift-numerics) includes modules named `ComplexModule` and `RealModule`.
