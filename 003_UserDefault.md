# UserDefault()



> MARK: Save Something With UserDefaults()
---


    @objc func saveTasks(){
        
        guard let text = field.text, !text.isEmpty  else{
            return
        }
        if let count = UserDefaults().value(forKey: "count") as? Int{
            let newCount = count + 1
            UserDefaults().set(newCount, forKey: "count")
            UserDefaults().set(text, forKey: "task_\(newCount)")
        }    
        navigationController?.popViewController(animated: true)  
    }
    
    
    
> MARK: Fetch Something With UserDefaults()
---
     for x in 0..<count {
            if let task = UserDefaults().value(forKey: "task_\(x+1)") as? String {
                tasks.append(task)
            }
        }
        
        tableView.reloadData()

> MARK: UserDefaults() is not a good way to save variables. It does not use logic of database. It only saves dictionary. It is only available for small data. CoreData is slower but better.
---
