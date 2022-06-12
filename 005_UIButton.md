# UIBUTTON

### class ViewController: UIViewController {


     private func setupNumberPad(){
        let buttonSize = view.frame.size.width / 4
        
        
> MARK: Buttons Are Ceated With For Loop
---

        for y in 0...2 {
            for x in 0...2 {
                let button1 = UIButton(frame: CGRect(x: buttonSize * CGFloat(x), y: holder.frame.size.height-(buttonSize*CGFloat((2+(y)))), width: buttonSize, height: buttonSize))
                button1.setTitleColor(.black, for: UIControl.State.normal)
                button1.backgroundColor = .white
                button1.setTitle("\(x+1+(3*y))", for: UIControl.State.normal)
                
> MARK: Buttons Are Assigned to Tags and Functions
>       
                button1.tag = (x+2)+(3*y)
                button1.addTarget(self, action: #selector(numberPressed(_:)), for: UIControl.Event.touchUpInside)
                
> MARK: Buttons Are Added to View (In this case, to a special view named "holder")

                holder.addSubview(button1)
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
