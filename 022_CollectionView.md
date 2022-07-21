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
    
### Arranging collectionView Frame

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
   
   func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
        
        return 30
    }
    
    
    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
        let cell = collectionView.dequeueReusableCell(withReuseIdentifier: CustomCollectionViewCell.identifier, for: indexPath) as! CustomCollectionViewCell
        cell.setName(label: "Custom: \(indexPath.row)")
        return cell
    }
    
    
    
