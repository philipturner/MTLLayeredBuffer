# MTLLayeredBuffer

A package encapsulating `MTLLayeredBuffer` from [ARHeadsetKit](https://github.com/philipturner/ARHeadsetKit). This type is not included in [ARHeadsetUtil](https://github.com/philipturner/ARHeadsetUtil) since it is distinct from the other utilities. For more about it, refer to [its article](https://github.com/philipturner/ARHeadsetKit/blob/main/docs/articles/layered-buffer.md) in the ARHeadsetKit [article series](https://github.com/philipturner/ARHeadsetKit/blob/main/docs/article-list.md).

## Example of usage

```swift
import Metal
import MTLLayeredBufferModule

enum LiDARScanLayer: MTLBufferLayer {
    case pointCloud
    case pointIDs
    
    static let bufferLabel = "LiDAR Scan Buffer"
    
    func getSize(capacity: Int) -> Int {
        switch self {
        case .pointCloud:
            return capacity * MemoryLayout<SIMD3<Float>>.stride
        case .pointIDs:
            return capacity * MemoryLayout<UInt64>.stride
        }
    }
}

let device: MTLDevice = ...
let numElements: Int = ...

var buffer: MTLLayeredBuffer<LiDARScanLayer> // options = .storageModePrivate by default
buffer = device.makeLayeredBuffer(capacity: numElements, options: .storageModeShared)

let pointCloud = buffer[.pointCloud].assumingMemoryBound(to: SIMD3<Float>.self)
let pointIDs   = buffer[.pointIDs].assumingMemoryBound(to: UInt64.self)

for i in 0..<numElements {
    pointCloud[i] = ...
    pointIDs[i] = ...
}
```
