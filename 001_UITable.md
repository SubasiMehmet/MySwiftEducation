#Class View Controller



    let tableView : UITableView = {
        let tableView = UITableView()
        tableView.register(WordsTableListViewCell.self, forCellReuseIdentifier: WordsTableListViewCell.identifier)
        tableView.register(AddRowTableViewCell.self, forCellReuseIdentifier: AddRowTableViewCell.identifier)
        return tableView
    }()

override func viewDidLoad() {
        super.viewDidLoad()

        view.addSubview(tableView)
        initSearchController()
    }
    
    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()
        
        tableView.delegate = self
        tableView.dataSource = self
        tableView.frame = CGRect()
    }
  
