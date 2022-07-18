# Grand Central Dispatch

## Working with Threads

---

> There are 4 different level GCD type.

1. User Interactive
2. User Initiate
3. Utility Queue
4. Background Queue

**These are ordered by priority type. For example, "User interactive" has the most priority than the others have.**

---

> GCD uses other threads without no need of our calculation. 

> The most important think about it: If you send the process to other thread, rest of the code will not wait for it and continue. We may not want to skip the process sometimes. (Most of times)


**To send to another thread with spesific qos (Quality of service) (1)**

    DispatchQueue.global(qos: .background).async { [weak self] in   }
    DispatchQueue.global(qos: .userInitiated).async { [weak self] in   }
    DispatchQueue.global(qos: .utility).async { [weak self] in   }
    DispatchQueue.global(qos: .userInteractive).async { [weak self] in   }
    
    
**To send to another thread with default qos (2)** 

    performSelector(inBackground: #selector(fetchJSON), with: nil)

Note: default qos's priority of perform selector is between "userInitiated" and ".utility"

---

**Take back to main thread (1)**

    DispatchQueue.main.async { [weak self] in   }
 
**Take back to main thread (2)**
 
    performSelector(onMainThread: #selector(showError), with: nil, waitUntilDone: false)
 
 
Note: #selector always accepts @obj func 


---

> Main challange about using other threads rather than main thread is that User Interface must be updated in main thread. If a function contains table view updating operation, it must be in main thread. Otherwise, program does not work.

**Here is an example**


    performSelector(inBackground: #selector(fetchJSON), with: nil)
      
    @objc func fetchJSON() {
        
       let urlString: String
            
        if navigationController?.tabBarItem.tag == 0 {
           urlString = "https://www.hackingwithswift.com/samples/petitions-1.json"
        }else{
           urlString = "https://www.hackingwithswift.com/samples/petitions-2.json"
        }
        
        if let url = URL(string: urlString) {
           if let data = try? Data(contentsOf: url){
               parse(json: data)
               holdSpare()
                return
            }

            performSelector(onMainThread: #selector(showError), with: nil, waitUntilDone: false)
         }
    }

**Showing error is taken to MainThread in the function which is running on another thread.


---

> **NOTES:**


1. Using another thread is the best practice for JSON processes.
2. Usin another thread is the best practice for filter operations in wide lists.
3. User Interface operations need to be run in Main Thread. Otherwise, it does not work.
4. To make operation in MainThread with tableView which is running in a function not inside of MainThread: 

    tableView.performSelector(onMainThread: #selector(UITableView.reloadData), with: nil, waitUntilDone: false)

5. Using threads is a professional approach but while doing it, needed to be careful.




