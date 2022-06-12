# Singleton Structure 

> SINGLETON STRUCTURE IS USED TO TRANSFER OBJECT TO ANY OTHER ViewController
---

> SWIFT CLASS FOR SINGLETON


> MARK: IN THIS SINGLETON MODEL, IT IS DESIRED **listName** and **listUUID** TRANSFER TO OTHER ViewController BY UPON OBJECT OF **sharedInstance**
---

    import Foundation

    class ListModel{
    
    static let sharedInstance = ListModel()
    
    var listName = ""
    var listUUID = UUID()
    
    private init(){}
    }

