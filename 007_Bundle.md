# Bundle

> Bundle is where the project is!

> With Bundle, the files inside of the project file can be accesses.
--- 


> Creating File Manager

    let fm = FileManager.default
    
> Creating Path

    let path = Bundle.main.resourcePath!
    
> Fetching All Items from the Bundle

    let items = try! fm.contentsOfDirectory(atPath: path)
    
> NOTE: Creating bundle, usage of ! is totally safe because every app needs to have a bundle (file directory)    

        
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
