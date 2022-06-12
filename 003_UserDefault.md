# UserDefault()



> MARK: SAVE SOMETHING WITH UserDefaults()
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
