Small Note: For now, there is no Closures.md file. It will explain what closure is. This is some more detailed something abotu closures.

## Capturing Closure with Trailing Closure


    let submitAction = UIAlertAction(title: "Submit", style: .default) {
            [weak self, weak ac] _ in   
            guard let answer = ac?.textFields?[0].text else {return}
            self?.submit(answer)
            }
        
    ac.addAction(submitAction)
    present(ac, animated: true)
        
    }
    

    func submit(_ answer: String){...}
    
    
 > "Weak Capturing" is a good solution to prevent "memory leakage". More detail writes in "013_Strong_Weak_Unowned.md" file.

**"in" is a compulsary usage**

**"_" might be a variable but there is no need in this example.**

    {
    [weak self, weak ac] _ in   
    guard let answer = ac?.textFields?[0].text else {return}
    self?.submit(answer)
    }
