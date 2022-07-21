# Collection View


**ViewController**

    class ViewController: UIViewController, UICollectionViewDataSource, UICollectionViewDelegate {
   
      private var collectionView: UICollectionView?
    
    
      override func viewDidLoad() {
        super.viewDidLoad()
        
        // Do any additional setup after loading the view.
        
> First Settings

        let layout = UICollectionViewFlowLayout()
        layout.scrollDirection = .vertical
        
        
        collectionView = UICollectionView(frame: .zero,  collectionViewLayout: layout)
        layout.itemSize = CGSize(width: (UIScreen.main.bounds.size.width / 3)-4, height: (UIScreen.main.bounds.size.width / 3)-4)
        layout.minimumLineSpacing = 1   //Alt Üst
        layout.minimumInteritemSpacing = 1  //Yan yana
        
        guard let collectionView = collectionView else {
            return
        }

> Delegate

        collectionView.register(CustomCollectionViewCell.self, forCellWithReuseIdentifier: CustomCollectionViewCell.identifier)
        collectionView.delegate = self
        collectionView.dataSource = self
        view.addSubview(collectionView)
        
        
    }
    
    ---
    
### Arranging collectionView Frame - Some Auto Layout Code

    override func viewSafeAreaInsetsDidChange() {
        
        if #available(iOS 11.0, *) {
            let window = UIApplication.shared.windows[0]
            
            let safeFrame = window.safeAreaLayoutGuide.layoutFrame
            collectionView!.frame = safeFrame
            /*
             topSafeAreaHeight = safeFrame.minY
             bottomSafeAreaHeight = window.frame.maxY - safeFrame.maxY
             */
        }
        
    }

---

### Functions

**Item Count**

   func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
        
        return 30
    }
    
    
**Return cell/item**

    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
        let cell = collectionView.dequeueReusableCell(withReuseIdentifier: CustomCollectionViewCell.identifier, for: indexPath) as! CustomCollectionViewCell
        cell.setName(label: "Custom: \(indexPath.row)")
        return cell
    }
    
    
    
**Insets of the cell**
    
    func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, insetForSectionAt section: Int) -> UIEdgeInsets {
    
    private let sectionInsets = UIEdgeInsets(top: 10,
                                             left: 10,
                                             bottom: 10,
                                             right: 10)
    
      return sectionInsets
    }
    
    
    
**Size of the cell**
    
        func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, sizeForItemAt indexPath: IndexPath) -> CGSize {
        /*
        let paddingSpace = sectionInsets.left * (itemsPerRow + 1)
        let availableWidth = view.frame.width - paddingSpace
        let widthPerItem = availableWidth / itemsPerRow
        */
        return CGSize(width: 140, height: 180)
        
    }
    
**DidSelect **

    override func collectionView(_ collectionView: UICollectionView, didSelectItemAt indexPath: IndexPath) {
        let person = people[indexPath.item]
        
        let questionAc = UIAlertController(title: "What is your purpose?", message: "", preferredStyle: .alert)
        let deleteButton = UIAlertAction(title: "Delete", style: UIAlertAction.Style.destructive) { [weak self] _ in
            
            self?.people.remove(at: indexPath.item)
            collectionView.reloadData()
        }
      }
    
>collectionView.reloadData()   
    
