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

### Precedence test  // Comparing Order -> Boolean

    if "aaa" < "bbb" { True }
    
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
