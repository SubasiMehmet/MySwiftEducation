#Bundle

> Bundle is where the project is!

> With Bundle, the files inside of the project file can be accesses.
--- 


    let fm = FileManager.default
    let path = Bundle.main.resourcePath!
    let items = try! fm.contentsOfDirectory(atPath: path)
        
> MARK: Adding the files' names (images' names) to the list as String
--- 
        for item in items {
            if item.hasPrefix("nssl"){
                pictures.append(item)
            }
            // MARK: Sort the array
            pictures.sort()
        }
        
    }
