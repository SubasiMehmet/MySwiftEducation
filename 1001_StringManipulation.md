# STRING MANIPULATION

### Initialize

    var emptyString = ""
    var anotherEmptyString = String()
    var optionalEmptyString : String?
    var asfasd : String = "Hola"
    var repeatingStr = String(repeating: "Hello", count: 4)   //Repeating String
    
### Multiline String

> Not multiline thanks to '\' and for the next line '\n' can be used in normal String. '\' is just used here for readibility.

    let longString = """
    Hello, \
    It will not pass into other line \
    This is a long line but not multiline.
    But this is next line
    """

    let nextLine = "Hello\nHow are you? \t I hope everyting is OK."

### Character
    
    var Char : Character = "A"
    var Char2 = greetings.first! as Character
    
### Merge Strings

    var hello = "Hello"
    var world = "World"
    hello += ", \(world)"

### Empty Test -> Boolean

    let boolean = hello.isEmpty

### Equality test -> Boolean

    if hello == world {}
    
### Prefix, Suffix, Contains -> Boolean

    let line  = "Some test data"
    line.hasPrefix("Some") // True
    line.hasSuffix("data") //True
    line.hasPrefix("some") // False
    line.contains("test") //True
    
    
### Uppercase - Lowercase

    let mixedCase = "ABCdef asf"
    let upperCased =  mixedCase.uppercased()
    let lowerCased = mixedCase.lowercased()
    let capitalizer = mixedCase.capitalized


### Spliting into SubString Array

    var greeting = "Hello, Merhaba, Hallo, Bonjour, Hola"
    var arr = greeting.split(separator: ",")

### Merge Substring Array to String

    var arr2 = arr.joined(separator: ", ")
    
### Substring & String Conversion

> Conversiton to each other is pretty easy like String(substr) or Substring(str). But otherwise, it will give an error.

> Substring may be created but that is not a normal way. If a String is splitted / divided / segmented, Substring is created with this way.

    var stringStr = String()
    var substringStr = Substring()

    stringStr = String(arr[1])    //arr[] is Substring Array from former example
    substringStr = arr[1]
    substringStr = Substring(stringStr)
    
### Clearing White Spaces & Extra Lines

     str.trimmingCharacters(in: .whitespacesAndNewlines)
     
### Processing char by char

    for character in swift {
        //print(character)
    }
    
### Shuffle String

>Shuffle() doesn't return anything. It change the String
>Shuffled returns a shuffled string and it need to be assigned to another one to hold that shuffled String.

    var shuffledSwift = swift.shuffled()
    shuffledSwift.shuffle()

    for i in swift.shuffled(){
      // Do something with "i"
    }

### Counting

> spain.utf16.count is the best practice.

    let spain = "España"
    spain.count                 // 6
    spain.unicodeScalars.count  // 6
    spain.utf16.count           // 6 is the best practice
    spain.utf8.count            // 7 because of the 'ñ'
    
### Character Control / Check

    let number : Character = "5"
    number.isNumber
    number.isLetter //To find letters, the best practice. It contains Ş,Ğ etc.
    number.isASCII
    number.isPunctuation
    number.isSymbol
    number.isNewline
    number.isWhitespace
    number.isMathSymbol
    number.isUppercase
    //number.is...
    
### English Alphabet Control

> char.isLetter contains all letters like "ñ, ş, ğ". But for the English alphabet, below example can be used.

    let char = "Ş"
    if (char >= "a" && char <= "z") || (char >= "A" && char <= "Z") {   // Returns false
        char 
    }

### Precedence test  // Comparing Order -> Boolean

> 'a' has lower ASCII value than 'b'. 

    if "aaa" < "bbb" { True }

### ASCII Check

    number.asciiValue

---
---

# String Index

### Index

> To select a special character, **index** needs to be used. Index doesn't return a Int. **Index is index!!!**

> To select a special character, str[index] needs to be used. str[1] cannot be used. **Because index is not a Integer!!!**

### startIndex & endIndex

> startIndex declares first character like [0] but end index doesn't declares last character. It declares one character after the last character.


** startIndex & endIndex are used frequently to select a char.

    let startIndex = str.startIndex     //It declares index
    let endIndex = str.endIndex         //It declares index
    
    let firstLetter = str[str.startIndex]
    //let endLetter = str[str.endIndex]     //It doesn't work directly. It declares after one index from the final letter. XXX


## str(index)

> I think, the following two are not a perfect choise beacuse there is offset option.

    str[str.index(after: str.startIndex)]   //"1" index after startIndex  -> Second Letter
    str[str.index(before: str.endIndex)]    //"1" index before endIndex   -> First Letter


### offset

> To select a char, **offset** is a better option.

    let str = "Hello"
    str[str.index(str.startIndex, offsetBy: 1)]    -> 'e'       // From the beginning, it starts with 0  !!!
    str[str.index(str.endIndex, offsetBy: -4)]     -> 'e'        // From the end, it starts with -1  !!!

> **Important Note: From the beginning, it starts with 0. From the end, it starts with -1.**

### limitedBy


> Index with optional -> To avoid error. 
 
> If we go too far with offset, it gives an error. But with limit, if it is go too far, index will be nil.

    let someIndex = str.index(str.startIndex, offsetBy: 120, limitedBy: str.endIndex)

### Process every character one by one with index
    
    for index in str.indices {
       //print(str[index])
    }

    for letter in str {     // without index
      //print(letter)
    }



### Drop First() & Last()

> Drop() doesn't drop in original text. It returns dropped string and needs to bes assigned to hold.


    let strDropFirst = str.dropFirst()  //Assigning
    let strDropFromFirst = str.dropFirst(2) //Assigning
    let strDropLast = str.dropLast()
    let strDropFromLast = str.dropLast(2)
    


### Finding A Character in String

> Finding first index -> If there is no letter, it would be nil.

    str.firstIndex(of: "W")
    str.lastIndex(of: "W")
    swift.first
    swift.last



### Remove

> // It removes the char, changes the original String and return removed char

    let removedLetter = str.remove(at: str.index(str.startIndex, offsetBy: 2)) 



## Index Range

**String[range]**

> **Range = lowerBound ... upperBound** OR **Range = lowerBound ..< upperBound** 

    let myString = "100dayswithswfit.com"

    let firstIndex = myString.startIndex
    let lastIndex = myString.index(myString.endIndex, offsetBy: -4)
    let range = firstIndex ..< lastIndex    // ..< OR ...
    let range2 = firstIndex ... lastIndex
    mySubString[range]
    mySubString[range2]

### Find Range of subString

    if let findSubstring = myString.range(of: "com") {
       //print(myString[findSubstring])
    }
