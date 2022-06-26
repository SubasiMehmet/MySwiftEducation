# NAVIGATION & BAR BUTTON ITEM

---
### Navigation Button

> It adds a Navigation Item that is written "Open" on the right upper side

    navigationItem.rightBarButtonItem = UIBarButtonItem(title: "Open", style: .plain, target: self, action: #selector(openTapped))

> This is a system button called "add" shaped "plus"  

    navigationItem.rightBarButtonItem = UIBarButtonItem(barButtonSystemItem: .add, target: self, action: nil)
        
        
        
        
        
        
        //MARK: - Toolbar Buttons / Items
        let spacer = UIBarButtonItem(barButtonSystemItem: .flexibleSpace, target: nil, action: nil)
        let refresh = UIBarButtonItem(barButtonSystemItem: .refresh, target: webView, action: #selector(webView.reload))
        let forward = UIBarButtonItem(title: "Forward", style: .plain, target: webView, action: #selector(webView.goForward))
        let backward = UIBarButtonItem(title: "Backward", style: .plain, target: webView, action: #selector(webView.goBack))
