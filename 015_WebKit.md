# WEBKIT

> It creates a easy browser.

> Start with import

    import UIKit
    import WebKit
    
 > Create a WKWebView variable
 
    var webView : WKWebView!

// It must precede viewDidLoad
**override func loadView {**   
    
        webView = WKWebView()
        webView.navigationDelegate = self
        view = webView
        
**}**
    
    
**override func viewDidLoad {**   



---
> **Loading URL**

> Force unwrap is best practice here for line 1

> Backward and forward specialization is added to page by sliding right and left for line 2
        
        let url = URL(string: "https://" + webSites[0])!  
        webView.load(URLRequest(url: url))
        webView.allowsBackForwardNavigationGestures = true  

                
        navigationItem.rightBarButtonItem = UIBarButtonItem(title: "Open", style: .plain, target: self, action: #selector(openTapped))

> Some Toolbar Buttons for WebView
     
        let spacer = UIBarButtonItem(barButtonSystemItem: .flexibleSpace, target: nil, action: nil)
        let refresh = UIBarButtonItem(barButtonSystemItem: .refresh, target: webView, action: #selector(webView.reload))
        let forward = UIBarButtonItem(title: "Forward", style: .plain, target: webView, action: #selector(webView.goForward))
        let backward = UIBarButtonItem(title: "Backward", style: .plain, target: webView, action: #selector(webView.goBack))

        
> Thanks to spacer button, refresh button is placed on the right // Just for extra information
 
        toolbarItems = [progressButton, spacer, backward, forward, refresh]
        navigationController?.isToolbarHidden = false
        
**}**
    
> For www.apple.com.tr, webView title is Apple.

     func webView(_ webView: WKWebView, didFinish navigation: WKNavigation!) {
        title = webView.title
    }
    
## Progress View Bar


var progressView : UIProgressView!

**override func viewDidLoad() {**

    progressView = UIProgressView(progressViewStyle: .default)
    progressView.sizeToFit()
    let progressButton = UIBarButtonItem(customView: progressView)
    
> KeyValue Observer for WKWebView.estimatedProgress

     webView.addObserver(self, forKeyPath: #keyPath(WKWebView.estimatedProgress), options: .new, context: nil)
    
**}**

> Change the loading progress regard of observer
>
    override func observeValue(forKeyPath keyPath: String?, of object: Any?, change: [NSKeyValueChangeKey : Any]?, context: UnsafeMutableRawPointer?) {
        if keyPath == "estimatedProgress" {
            progressView.progress = Float(webView.estimatedProgress)
        }
    }
    
## Web Site Allowance Policy

> If if host.contains(webSite) is not true, this website cannot be visited. (Host is like www.apple.com or apple.com)

    func webView(_ webView: WKWebView, decidePolicyFor navigationAction: WKNavigationAction, decisionHandler: @escaping (WKNavigationActionPolicy) -> Void) {
        
        let url = navigationAction.request.url
            if url!.absoluteString.range(of: "about:blank") != nil {
                decisionHandler(.cancel)
                return
            }
        
        //let url = navigationAction.request.url
        if let host = url?.host{
            for webSite in webSites {
                if host.contains(webSite){
                    decisionHandler(.allow)
                    return
                }
            }
        }
        
        giveAlert(title: "Blocked Website Trial", message: "This website has been blocked!")
        decisionHandler(.cancel)
    }
    
> if url!.absoluteString.range(of: "about:blank") != nil is controlled in this code because of some reason that I don't understand exatly, url returns "about:blank" sometimes.

