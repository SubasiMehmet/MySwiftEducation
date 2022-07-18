# UIBUTTON

### class ViewController: UIViewController {


     private func setupNumberPad(){
        let buttonSize = view.frame.size.width / 4
        
        
> MARK: Buttons Are Ceated With For Loop
---

        for y in 0...2 {
            for x in 0...2 {
                let button = UIButton(frame: CGRect(x: buttonSize * CGFloat(x), y: holder.frame.size.height-(buttonSize*CGFloat((2+(y)))), width: buttonSize, height: buttonSize))
                button.setTitleColor(.black, for: UIControl.State.normal)
                button.backgroundColor = .white
                button.titleLabel?.font = UIFont.systemFont(ofSize: 36)
                button.setTitle("WWW", for: .normal)
                button.layer.borderColor = UIColor.systemGray.cgColor
                button.layer.borderWidth = 1
                button.setTitle("\(x+1+(3*y))", for: UIControl.State.normal)
                
> MARK: Buttons Are Assigned to Tags and Functions
---
                button.tag = (x+2)+(3*y)
                button.addTarget(self, action: #selector(numberPressed(_:)), for: UIControl.Event.touchUpInside)
                
> MARK: Buttons Are Added to View (In this case, to a special view named "holder")
---
                holder.addSubview(button)
            }
        }
    }
    

> MARK: Buttons' Press Function Is Controlled With Tag. 

> Check the @objc func type. It is with parameter called sender. Because they are created with for, func needs to recognize them with their sender.
---
        @objc func numberPressed(_ sender: UIButton) {
        
        let tag  = sender.tag - 1
        //sender.flash()
        sender.pulsate()
        //print("clicked")
        
        if resultTextField .text == "0" {
            resultTextField.text = "\(tag)"
        }else if let text = resultTextField.text {
            resultTextField.text = text + "\(tag)"
        }
    }

---

> **sender**

    @objc func letterTapped(_ sender: UIButton) {
        guard let buttonTitle = sender.titleLabel?.text else {return}
        sender.isHidden = true
    }
    
    
## Auto Layout

     var myButton = UIButton()
  
     override func loadView()
          view = UIView()
          
        myButton = UIButton(type: .system)  // -> Important. Otherwise, system does not recognize the button.
        let buttonSize = UIScreen.main.bounds.size.height / 12
        myButton.translatesAutoresizingMaskIntoConstraints = false
        myButton.setTitle("OK", for: .normal)
        myButton.titleLabel?.font = UIFont.systemFont(ofSize: 30)
        myButton.backgroundColor = .white
        myButton.tintColor = .systemBlue
        myButton.layer.cornerRadius = 20
        myButton.layer.borderWidth = 1
        myButton.layer.borderColor = UIColor.systemGray.cgColor
        myButton.addTarget(self, action: #selector(giveLetter), for: .touchUpInside)
  
  
## Some Animation to Press Buttons
> MARK: For instance, It can be used like **sender.pulsate**
---

    extension UIButton {
    func pulsate() {
    let pulse = CASpringAnimation(keyPath: "transform.scale")
    pulse.duration = 0.4
    pulse.fromValue = 0.98
    pulse.toValue = 1.0
    pulse.autoreverses = false
    pulse.repeatCount = 0
    pulse.initialVelocity = 0.5
    pulse.damping = 1
    layer.add(pulse, forKey: nil)
    }

    // Not used for this app.
    func flash() {
    let flash = CABasicAnimation(keyPath: "opacity")
    flash.duration = 0.3
    flash.fromValue = 1
    flash.toValue = 0.1
    flash.timingFunction = CAMediaTimingFunction(name: CAMediaTimingFunctionName.easeInEaseOut)
    flash.autoreverses = false
    flash.repeatCount = 0
    layer.add(flash, forKey: nil)
    }
}
