# NAVIGATION & BAR BUTTON ITEM

---
### Navigation Button

> It adds a Navigation Item that is written "Open" on the right upper side

    navigationItem.rightBarButtonItem = UIBarButtonItem(title: "Open", style: .plain, target: self, action: #selector(openTapped))

> This is a system button called "add" shaped "plus"  

    navigationItem.rightBarButtonItem = UIBarButtonItem(barButtonSystemItem: .add, target: self, action: nil)
        
        
        
 ### Toolbar Buttons    
        
> It adds a Toolbar Button Item that is written "Open" on bottom

> Spacer is the pretty important to arranges button on toolbar. It gives space and fil all the other empty space.
 
        let spacer = UIBarButtonItem(barButtonSystemItem: .flexibleSpace, target: nil, action: nil)
        let refresh = UIBarButtonItem(barButtonSystemItem: .refresh, target: webView, action: #selector(webView.reload))
        let forward = UIBarButtonItem(title: "Forward", style: .plain, target: webView, action: #selector(webView.goForward))
        let backward = UIBarButtonItem(title: "Backward", style: .plain, target: webView, action: #selector(webView.goBack))

        
> Thanks to spacer button, refresh button is placed on the right

        toolbarItems = [backward, forward, spacer, refresh]
        
> Final setting
     
        navigationController?.isToolbarHidden = false
        
        
### Title & Appearance

https://developer.apple.com/documentation/uikit/uinavigationcontroller/customizing_your_app_s_navigation_bar


> Some extra settings

        self.title = "Strom Viewer"
        navigationController?.navigationBar.prefersLargeTitles = true
        
        navigationController?.hidesBarsOnSwipe = true
        navigationController?.hidesBottomBarWhenPushed = true
        navigationController?.hidesBarsOnTap = true
        
---  
        title = "Picture \(selectedImageNumber) of \(totalNumberOfImages)"
        navigationItem.largeTitleDisplayMode = .never
        
---

        override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        navigationController?.hidesBarsOnTap = true
        }
        
---
        if #available(iOS 15, *) {
                let appearance = UINavigationBarAppearance()
                appearance.configureWithOpaqueBackground()
             // appearance.backgroundColor = .systemGray
                navigationController?.navigationBar.standardAppearance = appearance
                navigationController?.navigationBar.scrollEdgeAppearance = navigationController?.navigationBar.standardAppearance
            }
            
---
---

> **A USEFUL EXTENSION**

**extension UIViewController / UITableViewController {**

    extension UITableViewController {
    func configureNavigationBar(titleColor: UIColor, backgoundColor: UIColor, tintColor: UIColor, title: String, preferredLargeTitle: Bool) {
   
    if #available(iOS 15.0, *) {
        let navBarAppearance = UINavigationBarAppearance()
        navBarAppearance.configureWithOpaqueBackground()
        navBarAppearance.largeTitleTextAttributes = [.foregroundColor: titleColor]
        navBarAppearance.titleTextAttributes = [.foregroundColor: titleColor]
        navBarAppearance.backgroundColor = backgoundColor

        navigationController?.navigationBar.standardAppearance = navBarAppearance
        navigationController?.navigationBar.compactAppearance = navBarAppearance
        navigationController?.navigationBar.scrollEdgeAppearance = navBarAppearance

        navigationController?.navigationBar.prefersLargeTitles = preferredLargeTitle
        navigationController?.navigationBar.isTranslucent = false
        navigationController?.navigationBar.tintColor = tintColor
        navigationItem.title = title

    } else {
        // Fallback on earlier versions
        navigationController?.navigationBar.barTintColor = backgoundColor
        navigationController?.navigationBar.tintColor = tintColor
        navigationController?.navigationBar.isTranslucent = false
        navigationItem.title = title
    }
    }}
        
>**THIS FUNCTION IS USED LIKE THIS:**

    configureNavigationBar(titleColor: .systemPurple, backgoundColor: .white, tintColor: .systemYellow, title: "My Shopping List", preferredLargeTitle: true)
