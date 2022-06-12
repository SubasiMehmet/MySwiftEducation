# CORE DATA


> Core Data works with Database logic. Thanks to Core Data, **large data** can be saved inside of the device.

> Furthermore, while fetching, data can be filtered and loaded.
---

### @objc func saveButtonTapped(){
        
        let appDelegate = UIApplication.shared.delegate as! AppDelegate
        let context = appDelegate.persistentContainer.viewContext
        
> MARK: Creating NSEntity with Entity Referance
---     
        let duties = NSEntityDescription.insertNewObject(forEntityName: "Duties", into: context)
        
> MARK: Attributes
---
        duties.setValue(listTextField.text, forKey: "duty")
        duties.setValue(UUID(), forKey: "id")
        
> MARK: Save CoreData
---     
        do{
            try context.save()
        }catch{
            print("Saving Problem Occured...")
        }
  ### }      
