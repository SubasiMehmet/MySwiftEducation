# UITable with Different Prototype Cells

## Class View Controller

    class WordsVC: UIViewController: UITableViewDelegate, UITableViewDataSource {

    let tableView : UITableView = {
        let tableView = UITableView()
        tableView.register(WordsTableListViewCell.self, forCellReuseIdentifier: WordsTableListViewCell.identifier)
        tableView.register(AddRowTableViewCell.self, forCellReuseIdentifier: AddRowTableViewCell.identifier)
        return tableView
    }()

    override func viewDidLoad() {
        super.viewDidLoad()

        view.addSubview(tableView)
    }
    
    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()
        
        tableView.delegate = self
        tableView.dataSource = self
        tableView.frame = CGRect()
    }
    
    }
    
======
    
   
    
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return 10
    }
    
======
    
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
   
======

    func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        if indexPath.row < 1 {
            return view.frame.height / 15
        }
        return view.frame.height / 12
    }
    
======

    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        let listModel = ListModel.sharedInstance
        listModel.listName = myListArray[indexPath.row]
        listModel.listUUID = myIdArray[indexPath.row]
        performSegue(withIdentifier: "toDetailVC", sender: nil)
    }
  
