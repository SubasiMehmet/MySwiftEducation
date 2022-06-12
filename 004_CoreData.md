# CORE DATA



> Core Data works with Database logic. Thanks to Core Data, **large data** can be saved inside of the device.

> Furthermore, while fetching, data can be filtered and loaded.
---
---
> Firstly, Make This Settings...
![Screen Shot 2022-06-12 at 18 17 23](https://user-images.githubusercontent.com/50085545/173240133-7400f622-b559-447b-8472-2c7e4c844538.png)
---
---


## Saving Core Data

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
## Fetching All Core Data


### class ViewController: UIViewController {

> MARK: - Empty Arrays to Update (Not about Core Data)
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
   
   
--- 
--- 
## Fetching & Deleting Filtered Core Data
    
    func tableView(_ tableView: UITableView, commit editingStyle: UITableViewCell.EditingStyle, forRowAt indexPath: IndexPath) {
        if editingStyle == .delete {
        
> MARK: Fetching Only That Result in Selected Row
---

            let appDelegate = UIApplication.shared.delegate as! AppDelegate
            let context = appDelegate.persistentContainer.viewContext
            
            let fetchRequest = NSFetchRequest<NSFetchRequestResult>(entityName: "Duties")
            fetchRequest.returnsObjectsAsFaults = false
            
> MARK: Filtering with UUID() While Fetching
---

            let idString = self.myIdArray[indexPath.row].uuidString
            fetchRequest.predicate = NSPredicate(format: "id = %@", idString)
            
            
> MARK: Fetching & Deleting from CoreData

> After deleting from CoreData, Delete it from array and reload UITable
---
            do{
                let results = try context.fetch(fetchRequest)
                if results.count > 0 {
                    for result in results as! [NSManagedObject] {
                        if let id = result.value(forKey: "id") as? UUID {
                            if id == myIdArray[indexPath.row] {
                                context.delete(result)
                                self.myListArray.remove(at: indexPath.row)
                                self.myIdArray.remove(at: indexPath.row)
                                self.myTableList.reloadData()
                                do {
                                    try context.save()
                                } catch {
                                    print("CoreData Saving Problem...")
                                }
                                break
                            }
                            
                        }
                    }
                }
               
                
            }catch {
                print("Some Filtering Problem...")
            }
              
        }
        
    }
    
