# Alert

---
> Creating Alert

    let alert = UIAlertController(title: "Current Score", message: "\(self.score)", preferredStyle: UIAlertController.Style.alert)
    let button = UIAlertAction(title: "OK", style: UIAlertAction.Style.default, handler: nil)
    alert.addAction(button)
    present(alert, animated: true)

> OR

        let alert = UIAlertController(title: title, message: "Your score is \(score)" , preferredStyle: UIAlertController.Style.alert)
        alert.addAction(UIAlertAction(title: "Continue", style: UIAlertAction.Style.default, handler: { handler in
            self.askQuestion()
        }))
        present(alert, animated: true)
        

> Creating alert after an alert. It uses like nested alert. Other alert is added to first one's button's action.
        
        let alert = UIAlertController(title: title, message: "Your score is \(score)", preferredStyle: UIAlertController.Style.alert)
        let finalButton = UIAlertAction(title: "Continue", style: UIAlertAction.Style.default, handler: nil)
        let okButton = UIAlertAction(title: "Continue", style: UIAlertAction.Style.default) { UIAlertAction in
            self.numberOfQuestion += 1
            if self.numberOfQuestion == 10 {
                let finalAlert = UIAlertController(title: "You Answered 10 Question", message: "Your final score is \(self.score)", preferredStyle: UIAlertController.Style.alert)
                finalAlert.addAction(finalButton)
                self.present(finalAlert, animated: true)
            }
        }
        alert.addAction(okButton)
        self.present(alert, animated: true, completion: nil)
        self.askQuestion()
        

> **Best practice to create alert is creating function like Alert(title: String, message: String)**


---

# ACTION SHEET

**MARK: - Action Sheet ve Adding Actions**
 
    @objc func openTapped(){
        let actionSheet = UIAlertController(title: "Open page...", message: nil, preferredStyle: .actionSheet)
        actionSheet.addAction(UIAlertAction(title: "apple.com", style: .default, handler: openPage))
        actionSheet.addAction(UIAlertAction(title: "hackingwithswift.com", style: .default, handler: openPage))
        actionSheet.addAction(UIAlertAction(title: "Cancel", style: .cancel))
        actionSheet.popoverPresentationController?.barButtonItem = navigationItem.rightBarButtonItem  // For iPads
        present(actionSheet, animated: true)
    }

> Giving action title as parameter to another function and managing handler

     func openPage(action: UIAlertAction){
        guard let actionTitle = action.title else {return}
        if let url = URL(string: "https://" + actionTitle) {
            webView.load(URLRequest(url: url))
        }
