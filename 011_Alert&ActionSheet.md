# Alert


> MARK: Creating alert after an alert. It uses like nested alert. Other alert is added to first one's button's action.
        
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
