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


# String Index
