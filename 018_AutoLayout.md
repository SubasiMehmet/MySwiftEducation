# AUTO-LAYOUT

![Screen Shot 2022-07-02 at 20 11 37](https://user-images.githubusercontent.com/50085545/177215651-e4ab5a70-6d42-49cc-b3e0-4150b5dbc85d.png)

---
https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AutolayoutPG/VisualFormatLanguage.html#//apple_ref/doc/uid/TP40010853-CH27-SW1
---
https://stackoverflow.com/questions/54047396/how-to-use-visual-format-language-to-set-constraints-in-swift
---        
        // MARK: - Multiply view.widthAnchor with 0.2 and add (-10)
          label1.heightAnchor.constraint(greaterThanOrEqualTo: view.widthAnchor, multiplier: 0.2, constant: -10).isActive = true
        // This ruins the view.
        // MARK: - Moreover
        // view.frame.widt OR view.safeAreaLayoutGuide.layoutFrame.width give the width as constant Double.
        
        
        
        //MARK: Make all label's height same. We did not determine any specific height. (Greater then 30)
        for label in [label2, label3, label4, label5] {
            label.heightAnchor.constraint(equalTo: label1.heightAnchor).isActive = true
        }
        
        
        var previous : UILabel?

        for label in[label1, label2, label3, label4, label4, label5] {
            // MARK: Make all label's height equal to width of view.
            //label.widthAnchor.constraint(equalTo: view.widthAnchor).isActive = true
            //OR
            
            // MARK: It is negative!!! Because (equalTo: "A" and constant "B"( always says that the distance start from "A" and go rightward by "B"
            label.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -50).isActive = false  //This is intentionally False.
            
            // MARK: These's priorities are not 1000 because of safeArea constraint.
            let trailingConstraint = label.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: 0)
            trailingConstraint.priority = UILayoutPriority(999)
            trailingConstraint.isActive = true

            let leadingConstraint = label.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 0)
            leadingConstraint.priority = UILayoutPriority(999)
            leadingConstraint.isActive = true
            
            // MARK: To stay in safe area from right and left side.
            label.trailingAnchor.constraint(equalTo: view.safeAreaLayoutGuide.trailingAnchor, constant: 0).isActive = true
            label.leadingAnchor.constraint(equalTo: view.safeAreaLayoutGuide.leadingAnchor, constant: 0).isActive = true
            
         
            //MARK: After for loop, by assigning label to last one, it leaves space between each other.
            //MARK: But for the first one, there is no previous and it goes to "else".
            if let previous = previous {
                label.topAnchor.constraint(equalTo: previous.bottomAnchor, constant: 40).isActive = true
                
            }else{
                //MARK: To stay in safe area from top side.
                label.topAnchor.constraint(equalTo: view.safeAreaLayoutGuide.topAnchor, constant: 0).isActive = true
            }
            
            previous = label
        }
        
        // MARK: To stay in safe area from bottom.
         label5.bottomAnchor.constraint(greaterThanOrEqualTo: view.safeAreaLayoutGuide.bottomAnchor, constant: 0).isActive = true
         label5.bottomAnchor.constraint(lessThanOrEqualTo: view.safeAreaLayoutGuide.bottomAnchor, constant: -10).isActive = false //This is intentionally False.

     
        
        
        //MARK: -
//        Every UIView has a set of anchors that define its layouts rules. The most important ones are widthAnchor, heightAnchor, topAnchor, bottomAnchor, leftAnchor, rightAnchor, leadingAnchor, trailingAnchor, centerXAnchor, and centerYAnchor.
//
//        Most of those should be self-explanatory, but it’s worth clarifying the difference between leftAnchor, rightAnchor, leadingAnchor, and trailingAnchor.
//        For me, left and leading are the same, and right and trailing are the same too.
//        MARK: leftAnchor = leadingAnchor  &  rightAnchor = trailingAnchor
