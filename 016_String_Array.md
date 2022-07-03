# STRING FEATURES

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

## insert(String:, at:)

> It add an item to where you want.
