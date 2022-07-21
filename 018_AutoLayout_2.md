# Auto Layout

## NSLayoutConstraint.activate


**override func loadView() {**

**UIScreen.main.bounds.size.height** might be used to reach size of screen.

    NSLayoutConstraint.activate([
            scoreLabel.topAnchor.constraint(equalTo: view.layoutMarginsGuide.topAnchor),
            scoreLabel.trailingAnchor.constraint(equalTo: view.layoutMarginsGuide.trailingAnchor),

            cluesLabel.topAnchor.constraint(equalTo: scoreLabel.bottomAnchor),
            cluesLabel.leadingAnchor.constraint(equalTo: view.layoutMarginsGuide.leadingAnchor, constant: 100),
            cluesLabel.widthAnchor.constraint(equalTo: view.layoutMarginsGuide.widthAnchor, multiplier: 0.6, constant: -100),
            
            answersLabel.topAnchor.constraint(equalTo: scoreLabel.bottomAnchor),
            answersLabel.trailingAnchor.constraint(equalTo: view.layoutMarginsGuide.trailingAnchor, constant: -100),
            answersLabel.widthAnchor.constraint(equalTo: view.layoutMarginsGuide.widthAnchor, multiplier: 0.4, constant: -100),
            answersLabel.heightAnchor.constraint(equalTo: cluesLabel.heightAnchor),
            
            currentAnswer.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            currentAnswer.widthAnchor.constraint(equalTo: view.widthAnchor, multiplier: 0.5),
            currentAnswer.topAnchor.constraint(equalTo: cluesLabel.bottomAnchor, constant: 20),
            
            submit.topAnchor.constraint(equalTo: currentAnswer.bottomAnchor),
            submit.centerXAnchor.constraint(equalTo: view.centerXAnchor, constant: -100),
            submit.heightAnchor.constraint(equalToConstant: 44),
            
            clear.centerXAnchor.constraint(equalTo: view.centerXAnchor, constant: 100),
            clear.centerYAnchor.constraint(equalTo: submit.centerYAnchor),
            clear.heightAnchor.constraint(equalTo: submit.heightAnchor),
            
            buttonsView.widthAnchor.constraint(equalToConstant: 750),
            buttonsView.heightAnchor.constraint(equalToConstant: 320),
            buttonsView.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            buttonsView.topAnchor.constraint(equalTo: submit.bottomAnchor, constant: 20),
            buttonsView.bottomAnchor.constraint(equalTo: view.layoutMarginsGuide.bottomAnchor, constant: -20)
            
                                    ]) 
                                    
> view.layoutMarginsGuide -> SafeAreaLayoutGuide

> layoutMarginsGuide and safeAreaLayoutGuide are NOT exacly the same thing. Not quite: layoutMarginsGuide is inside the safeAreaLayoutGuide, so it will be slightly smaller.
  
 ---
 
 > To set priority of an height or width, **while creating item**, this can be added.
 
    myLabel.setContentHuggingPriority(UILayoutPriority(1), for: .vertical)
    
> **OR**
    
    let centerY = title.centerYAnchor.constraint(equalTo: view.centerYAnchor)
    let spacing = title.topAnchor.constraint(greaterThanOrEqualTo: image.bottomAnchor, constant: 30)
    centerY.priority = UILayoutPriority(999)

    NSLayoutConstraint.activate([
      centerY,
      spacing
    ])
 
 ---
 
 
> Just to remember
 
    let constraintTrailing = containerView.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: 0.0)
    constraintTrailing.priority = UILayoutPriority(rawValue: 750.0)
    constraintTrailing.isActive = true
    
            
## override func loadView() 

> view = UIView() makes view equal to all view. 

        override func loadView() {
        
        view = UIView()
        view.backgroundColor = .white

---

        scoreLabel = UILabel()
        scoreLabel.translatesAutoresizingMaskIntoConstraints = false  // To make arrangement in layout. IMPORTANT!!!
        scoreLabel.textAlignment = .right
        scoreLabel.text = "Score: 0"
        view.addSubview(scoreLabel)
        
---

        let buttonsView = UIView()
        buttonsView.translatesAutoresizingMaskIntoConstraints = false
        view.addSubview(buttonsView)
  
--

**Following Safe Area**

> With this code piece, we can take safe area's coordinat or frame

    override func viewSafeAreaInsetsDidChange() {
        
        if #available(iOS 11.0, *) {
            let window = UIApplication.shared.windows[0]
            
            let safeFrame = window.safeAreaLayoutGuide.layoutFrame
            collectionView!.frame = safeFrame  
            /*
             topSafeAreaHeight = safeFrame.minY
             bottomSafeAreaHeight = window.frame.maxY - safeFrame.maxY
             */
        }
        
    }
