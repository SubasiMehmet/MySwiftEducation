# STRING FEATURES

---
## UITextChecker()

> UITextChecker() controls misspelling in a text. If it cannot find any misspelling in the text, it returns **"NSNotFound"**


    func misspelling(word: String) -> Bool {
        let checker = UITextChecker()
        let range = NSRange(location: 0, length: word.utf16.count)
        let misspelledRange = checker.rangeOfMisspelledWord(in: word, range: range, startingAt: 0, wrap: false, language: "en")
        return misspelledRange.location == NSNotFound
    }
