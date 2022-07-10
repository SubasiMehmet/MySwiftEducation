# didSet & willSet

##Property Observer

> In the below example, everytime when score changes, code will run inside of **{}**

    var score = 0 {
        didSet { //willSet
            scoreLabel.text = "Score: \(score)"
        }
    }
    
    
> With **didSet**, it will run the code after the property changes and with **willSet**, it will run the code before property changes.
