# Data Transfer Between View Controller _ BACK - FORWARD

> **There are some methods to transfer data**

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

---
---
## 3. Delegation (2 -> 1)

> Protocol is necessary

**Protocol**

    protocol DataTransferrable {
    func onEmergencyStatus(phoneNumber: String)
    }
    
**SecondVC {**

    var emergencyDelegateVariable : DataTransferrable?
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
        @IBAction func emergencyBtnPressed(_ sender: UIButton) {
            dismiss(animated: true) 
            self.emergencyDelegateVariable?.onEmergencyStatus(phoneNumber: sender.titleLabel!.text!)
        }
  
**}**


**ViewController {**

    @IBOutlet var myLabel: UILabel!
    

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view. 
    }
    
    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        if segue.identifier == "delegationSegue" {
            if let secondVC = segue.destination as? SecondVC {
                secondVC.emergencyDelegateVariable = self
            }
        }
    }

    
    func onEmergencyStatus(phoneNumber: String) {
        myLabel.text = phoneNumber
        print("Acil bir durumda \(phoneNumber) numarasını arayın")
    }

**}**


## 4. Closure (2 -> 1)

> Protocol is not used but it is not a perfect way to increase readability of the code.

    
**SecondVC {**

    var dataTransferClosure: ((String) -> Void)?
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }

    @IBAction func GoBack(_ sender: UIButton) {
        dismiss(animated: true) { [weak self] in
            self?.dataTransferClosure?(sender.titleLabel!.text!)
            //self?.dataTransferClosure?((sender.titleLabel?.text!)!)
            
        }
    }
    
**}**


**ViewController {**

    @IBOutlet var myLabel: UILabel!
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }
    
    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        if segue.identifier == "toSecondVC" {
            if let secondVC = segue.destination as? SecondVC {
                secondVC.dataTransferClosure = { [weak self] phoneNumber in
                    self?.myLabel.text = phoneNumber
                }
            }
        }
    }

**}**




