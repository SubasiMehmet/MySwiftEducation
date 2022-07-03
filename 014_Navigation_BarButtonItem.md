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
        
