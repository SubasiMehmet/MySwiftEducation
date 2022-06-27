# WEBKIT

> It creates a easy browser.

> Start with import

    import UIKit
    import WebKit
    
 > Create a WKWebView variable
 
    var webView : WKWebView!
    
> **override func loadView**   //It must precede viewDidLoad

    override func loadView() {
        super.loadView()
    
        webView = WKWebView()
        webView.navigationDelegate = self
        view = webView
        
    }
    
    
> **override func viewDidLoad**   

    override func viewDidLoad() {

---
> **Loading URL**
> Force unwrap is best practice here for line 1
> Backward and forward specialization is added to page by sliding right and left for line 2
        
        let url = URL(string: "https://" + webSites[0])!  
        webView.load(URLRequest(url: url))
        webView.allowsBackForwardNavigationGestures = true  

                
        navigationItem.rightBarButtonItem = UIBarButtonItem(title: "Open", style: .plain, target: self, action: #selector(openTapped))

> MARK: - Some Toolbar Buttons for WebView
     
        let spacer = UIBarButtonItem(barButtonSystemItem: .flexibleSpace, target: nil, action: nil)
        let refresh = UIBarButtonItem(barButtonSystemItem: .refresh, target: webView, action: #selector(webView.reload))
        let forward = UIBarButtonItem(title: "Forward", style: .plain, target: webView, action: #selector(webView.goForward))
        let backward = UIBarButtonItem(title: "Backward", style: .plain, target: webView, action: #selector(webView.goBack))

> MARK: - ProgressView Button on Toolbar for WebView

        progressView = UIProgressView(progressViewStyle: .default)
        progressView.sizeToFit()
        let progressButton = UIBarButtonItem(customView: progressView)
        
> MARK: Thanks to spacer button, refresh button is placed on the right // Just for extra information
 
        toolbarItems = [progressButton, spacer, backward, forward, refresh]
        navigationController?.isToolbarHidden = false
        
//MARK: KeyValue Observer for WKWebView.estimatedProgress

        webView.addObserver(self, forKeyPath: #keyPath(WKWebView.estimatedProgress), options: .new, context: nil)
      

    }
