# STRING & ARRAY FEATURES

---
## UITextChecker()

> UITextChecker() controls misspelling in a text. If it cannot find any misspelling in the text, it returns **"NSNotFound"**


    func isItTrue(word: String) -> Bool {
        let checker = UITextChecker()
        let range = NSRange(location: 0, length: word.utf16.count)
        let misspelledRange = checker.rangeOfMisspelledWord(in: word, range: range, startingAt: 0, wrap: false, language: "en")
        return misspelledRange.location == NSNotFound
    }

---
## utf16

> str.utf16.count is a better way than str.count

> For example "±" might have 3 letter in real or as a format of UTF-32. .count method count it as 3 letter but .utf16 does not. It counts it as just 1 "one

>Example is reacheable above, in the section of UITextChecker()

## firstIndex(of: )

> returns 10 because that's where wonderful starts at

    let someString = "This is a wonderful day"
    let index = someString.firstIndex(of: "wonderful")! 


## contains()

> Return Boolean


## remove(at: )

> It removes at that place.

## append()

> It add an item to end of the list

## appending()

> It add an item to end of the list but doesn't change the list. It returns a new list.

## insert(String:, at:)

> It add an item to where you want.

## components(separatedBy: "\n")

> It splits the text by a char (**for example: "\n"**) character and assings to a array.

    var splitAnswers = answersLabel.text?.components(separatedBy: "\n")
    
## split(separated: \n)

> It splits the text by a char (**for example: "\n"**) character and assings to a array.

    var splitAnswers = answersLabel.text?.split(separated: "\n")

## joined(separator: )

> It merges all array by putting a char (**for example: "\n"**) and makes a text (String)

    answersLabel.text = splitAnswers?.joined(separator: "\n")
    
## shuffle()

> It shuffles the array and creates new array.
        
        array.shuffle()

## shuffled()

> It shuffles the array and returns new array.
        let newArray = array.shuffled()
        
## removeAll & removeAll(keepingCapasity: Bool) 

> removeAll() removes all items in an array. 

> removeAll(keepingCapasity: Bool) removes all items in an array while let decide to hold memory for array. Not a really big difference.
