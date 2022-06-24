# Data Transfer Between View Controller _ BACK - FORWARD

> **There are some method to transfer data**

1. Variable Direct Transfer (1 -> 2)
2. Segue (1 -> 2)
3. Delegation (2 -> 1)
4. Closure (2 -> 1)
5. Singleton (1 -> 2)

> In this page, Singleton Method will not be covered.

---

## 1. Variable Direct Transfer (1 -> 2)

**ViewController {**

    let textToTransfer = "Hello World"
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    @IBAction func goToSecondVC(_ sender: Any) {
        
        let secondVC = storyboard?.instantiateViewController(withIdentifier: "SecondVC") as! SecondVC
        secondVC.transferredText = textToTransfer
        present(secondVC, animated: true)
        
    }
**}**


**SecondVC {**

    @IBOutlet var myLabel: UILabel!
    var transferredText = ""
    
    override func viewDidLoad() {
        super.viewDidLoad()
        myLabel.text = transferredText
    }
**}**


---
---
## 2. Segue (1 -> 2)

> Pretty Similar / Almost Same With First Method

**ViewController {**

    var textToTransfer = "Hello World!"
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        if segue.identifier == "goToSecondVC" {
            if let secondVC = segue.destination as? secondVC {
                secondVC.transferredText = textToTransfer
            }
        }
    }  
**}**


**SecondVC {**

    @IBOutlet var myLabel: UILabel!
    var transferredText = ""
    
    override func viewDidLoad() {
        super.viewDidLoad()     
        myLabel.text = transferredText 
    }
**}**

