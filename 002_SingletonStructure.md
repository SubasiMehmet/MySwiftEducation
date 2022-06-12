# Singleton Structure 

> SINGLETON STRUCTURE IS USED TO TRANSFER OBJECT TO ANY OTHER ViewController
---

> SWIFT CLASS FOR SINGLETON


> MARK: IN THIS SINGLETON MODEL, IT IS DESIRED TO TRANSFER **listName** and **listUUID** TO ANY OTHER ViewController BY USING OBJECT OF **sharedInstance**
---

    import Foundation

    class ListModel{
    
    static let sharedInstance = ListModel()
    
    var listName = ""
    var listUUID = UUID()
    
    private init(){}
    }

