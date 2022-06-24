# Data Transfer Between View Controller _ BACK - FORWARD

> **There are some method to transfer data**

1. Variable Direct Transfer
2. Segue
3. Delegation
4. Closure
5. Singleton

> In this page, Singleton Method will not be covered.

---

## Variable Direct Transfer (1 -> 2)

**ViewController {

    let textToTransfer = "Hello World"
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    @IBAction func goToSecondVC(_ sender: Any) {
        
        let secondVC = storyboard?.instantiateViewController(withIdentifier: "SecondVC") as! SecondVC
        secondVC.transferredText = textToTransfer
        present(secondVC, animated: true)
        
    }
**}


**SecondVC {

    @IBOutlet var myLabel: UILabel!
    var transferredText = ""
    
    override func viewDidLoad() {
        super.viewDidLoad()
        myLabel.text = transferredText
    }
**}
