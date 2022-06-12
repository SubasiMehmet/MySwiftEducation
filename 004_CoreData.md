# CORE DATA


> Core Data works with Database logic. Thanks to Core Data, **large data** can be saved inside of the device.

> Furthermore, while fetching, data can be filtered and loaded.
---

    @objc func saveButtonTapped(){
        
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
    }      


--- 
--- 

### class ViewController: UIViewController {

> MARK: - Fetch CoreData
---  

    @objc func getData() {
        
        myIdArray.removeAll(keepingCapacity: false)
        myListArray.removeAll(keepingCapacity: false)
        
        
> MARK: - Creating variable for CoreData
> ---

        let appDelegate = UIApplication.shared.delegate as! AppDelegate
        let context = appDelegate.persistentContainer.viewContext
        
> MARK: Creating Fetch with Entity Referance
---

        let fetchRequest = NSFetchRequest<NSFetchRequestResult>(entityName: "Duties")
        fetchRequest.returnsObjectsAsFaults = false    //Speed fetching process up
        
> MARK: Fetching Values and Adding to Arrays in a For Loop
---

        do{
            let results = try context.fetch(fetchRequest)
            
            for result in results as! [NSManagedObject] {
                if let newDuty = result.value(forKey: "duty") as? String {
                    self.myListArray.append(newDuty)
                    
                    if let newId = result.value(forKey: "id") as? UUID {
                        self.myIdArray.append(newId)
                    }
                }
            }
        }catch{
            print("Some Fetching Problem...")
        }
        self.myTableList.reloadData()
        
    }
