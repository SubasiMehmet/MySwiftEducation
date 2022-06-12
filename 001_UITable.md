# UITable with Different Prototype Cells

### class WordsVC: UIViewController: UITableViewDelegate, UITableViewDataSource {

---
> PRE-NOTE
#### viewDidLoad
#### viewDidLayoutSubviews
#### layoutSubviews
---

    let tableView : UITableView = {
        let tableView = UITableView()
        tableView.register(WordsTableListViewCell.self, forCellReuseIdentifier: WordsTableListViewCell.identifier)
        tableView.register(AddRowTableViewCell.self, forCellReuseIdentifier: AddRowTableViewCell.identifier)
        return tableView
    }()


> MARK: - UITABLEVIEW IS CREATED AS VARIABLE

> **viewDidLoad**

---

    override func viewDidLoad() {
        super.viewDidLoad()

        view.addSubview(tableView)
    }
    

> MARK: - UITABLEVIEW IS ADDED LIKE THIS BECAUSE IT IS A SUBVIEW

> **viewDidLayoutSubviews**
---

    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()
        
        tableView.delegate = self
        tableView.dataSource = self
        tableView.frame = CGRect()
    }
    
    }
    

> MARK: - DETERMINE THAT UITABLE RETURN HOW MANY CELLS
 ---
   
       
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return 10
    }
    

> MARK: - CELL CONTENT

> MARK: - DECIDE FOR EACH ROW WITH IF STATEMENT BY USING PROTOTYPE CELLS CLASSES
 ---
   
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        
        if indexPath.row < 1 {
            let cell = tableView.dequeueReusableCell(withIdentifier: WordsTableSearchTableViewCell.identifier, for: indexPath) as! WordsTableSearchTableViewCell
                cell.configure()
           
                cell.layer.borderWidth = 1
                cell.layer.borderColor = UIColor.white.cgColor
                return cell
            
        }
        if indexPath.row < 5{
            let cell = tableView.dequeueReusableCell(withIdentifier: AddRowTableViewCell.identifier, for: indexPath) as! AddRowTableViewCell
            return cell
            
        }else{
           
            let cell = tableView.dequeueReusableCell(withIdentifier: WordsTableListViewCell.identifier, for: indexPath) as! WordsTableListViewCell
            cell.myCategoryNameLabel.text = categoryNameArray[indexPath.row]
            cell.myImageView.image = categoryImageArray[indexPath.row]
            return cell
        }
    }
   

> MARK: - CELL HEIGHT
---

    func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        if indexPath.row < 1 {
            return view.frame.height / 15
        }
        return view.frame.height / 12
    }
    

> MARK: - WHAT WILL HAPPEN WHEN THAT ROW IS SELECTED
---

    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        let listModel = ListModel.sharedInstance
        listModel.listName = myListArray[indexPath.row]
        listModel.listUUID = myIdArray[indexPath.row]
        performSegue(withIdentifier: "toDetailVC", sender: nil)
    }
    

> MARK: - DELETE A ROW IN THE UITABLE

> MARK: - THIS ONLY SHOW ANIMATIOS. ARRAY SHOULD BE ARRANGED AGAIN WITH SELECTED ROW LIKE BELOW
---

    func tableView(_ tableView: UITableView, commit editingStyle: UITableViewCell.EditingStyle, forRowAt indexPath: IndexPath) {
        if editingStyle == .delete {
        
            // MARK: Fetching Only That Result in Selected Row
            let appDelegate = UIApplication.shared.delegate as! AppDelegate
            let context = appDelegate.persistentContainer.viewContext
            
            let fetchRequest = NSFetchRequest<NSFetchRequestResult>(entityName: "Duties")
            fetchRequest.returnsObjectsAsFaults = false
            
            //MARK: Filtering with UUID() While Fetching
            let idString = self.myIdArray[indexPath.row].uuidString
            fetchRequest.predicate = NSPredicate(format: "id = %@", idString)
            
            
            // MARK: Fetching & Deleting from CoreData
            //After deleting from CoreData, Delete it from array and reload UITable
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
 
---
---
    
### class WordsTableListViewCell: UITableViewCell {
    

> MARK: - IDENTIFIER IS THE MOST IMPORTANT ISSUE ABOUT TABLEVIEWCELL
---
    
    static let identifier = "WordsTableViewCell"
    

> MARK: - ADDING SOMETHING AS SUBVIEW INSIDE OF THE CELL
 ---

    var myImageView : UIImageView = {
        let imageView = UIImageView()
        imageView.image = UIImage(named: "Flintstone")
        imageView.contentMode = .scaleAspectFit
        return imageView
    }()
    

> MARK: - INITIALIZER OF TABLEVIEWCELL

> MARK: - IT IS ADDED ALWAYS // (There are some different ways to create but this is enough)
---


    override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
        super.init(style: style, reuseIdentifier: reuseIdentifier)
        
        contentView.addSubview(myImageView)
        contentView.addSubview(myCategoryNameLabel)
        contentView.addSubview(myCompletionLabel)
    }
    
    
> MARK: - ORGANAZING THE CELL

> **layoutSubviews**
---    
        override func layoutSubviews() {
        super.layoutSubviews()
        
        
        myImageView.frame = CGRect(x: 5,
                                   y: 5,
                                   width: (contentView.frame.size.width / 7),
                                   height: contentView.frame.size.height - 6)
                                   
        let myImageViewFrame = myImageView.frame
        
        myImageView.layer.masksToBounds  = true
        myImageView.layer.cornerRadius = 40
        
        myCategoryNameLabel.frame = CGRect(x: myImageViewFrame.maxX + 15,
                                           y: myImageViewFrame.minY,
                                           width: contentView.frame.size.width / 1.56 ,
                                           height: myImageViewFrame.height)
        
        let myCategoryNameLabelFrame = myCategoryNameLabel.frame

    }
    
