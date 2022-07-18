# UITextField


    class ViewController: UIViewController, UITextFieldDelegate {
    
    var myTextField = UITextField()
    
      override func loadView() {
        view = UIView()
      
        myTextField.translatesAutoresizingMaskIntoConstraints = false
        myTextField.textAlignment = .center
        myTextField.font = UIFont.systemFont(ofSize: 30)
        myTextField.layer.borderWidth = 0.5
        myTextField.layer.cornerRadius = 10
        myTextField.becomeFirstResponder()
        
        myTextField.addTarget(self, action: #selector(textViewChanged), for: .editingChanged)  -> It observes changes in the text and before any change, it call "textViewChanged" function. IMPORTANT!!!

        view.addSubview(myTextField)
      }
      
      
      override func viewDidLoad() {
        self.myTextField.delegate = self
      }
      
>**It forces textField to write lowercase**
>**It forces textField to write only one character**

    @objc func textViewChanged(){
        if let lowerCasedStr  = submitLabel.text?.lowercased{
            myTextField.text = lowerCasedStr()
        }
        
        guard let text = submitTextField.text else{return}
        if text.utf16.count == 2 {
            let droppedText = text.dropLast()
            submitTextField.text = String(droppedText)
        }
        
      }

>**It assigns "send"/"ok" key to function of "giveLetter()"**

    func textFieldShouldReturn(_ textField: UITextField) -> Bool {
        giveLetter()
        return true
    }
    
    
    
# UILabel
  
    override func loadView() {
        view = UIView()  
        
        myLabel.translatesAutoresizingMaskIntoConstraints = false
        myLabel.textAlignment = .center
        myLabel.font = UIFont.systemFont(ofSize: 30)
        myLabel.numberOfLines = 0   ->It allows to label wrap as much as possible. (0 = Infinite, 1 = One, 10 = Ten...)
        view.addSubview(myLabel)
    }
