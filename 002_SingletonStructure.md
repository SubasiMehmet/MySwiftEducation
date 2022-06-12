# Singleton Structure 

> SINGLETON STRUCTURE IS USED TO TRANSFER OBJECT TO ANY OTHER ViewController
---

> SWIFT CLASS FOR SINGLETON


> MARK: IN THIS SINGLETON MODEL, IT IS DESIRED TO TRANSFER **listName** and **listUUID** TO ANY OTHER ViewController BY USING OBJECT OF **sharedInstance**
---


### class ListModel{
    
    static let sharedInstance = ListModel()
    
    var listName = ""
    var listUUID = UUID()
    
    private init(){}
    }
    
 ---  
 ---
 
 
### class ViewController: UIViewController {

> MARK: ASSIGNING THE VARIABLE TO SINGLETON IN ORDER TO PREPARE TRANSFERING
---

    @objc func addButtonTapped() {
   
        let listModel = ListModel.sharedInstance
        listModel.listName = "Duty"
        performSegue(withIdentifier: "toDetailVC", sender: nil)
        
    }

// In this example, when a button is clicked, singleton runs.

---  
---
 
### class DetailVC: UIViewController, UINavigationControllerDelegate {

> MARK: FETCHING THE VALUE BY USING SINGLETON
---

**viewWillAppar**

    override func viewWillAppear(_ animated: Bool) {
        self.listTextField.text = ListModel.sharedInstance.listName
        self.UUIDTextLabel.text = ListModel.sharedInstance.listUUID.uuidString
    
    }
    
    
> MARK: THERE ARE SOME OTHER WAYS TO TRANSFER DATA LIKE **"PrepareForSegue"**, BUT SINGLETON IS THE BEST WAY.
---
    
