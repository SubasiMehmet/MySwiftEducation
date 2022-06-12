# Singleton Structure 

> SINGLETON STRUCTURE IS USED TO TRANSFER OBJECT TO ANY OTHER ViewController
---

> SWIFT CLASS FOR SINGLETON
---

```
import Foundation
```

class ListModel{
    
    static let sharedInstance = ListModel()
    
    var listName = ""
    var listUUID = UUID()
    
    
    private init(){}
}
