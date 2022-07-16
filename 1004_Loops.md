# For Loop

> **For loop can be named / labeled**

### label: for i in range/array/String where (condition)

> Note: if conditions also can be labeled.

    let languages = ["Türkçe", "İngilizce", "Almanca", "Fransızca"]

    languageFor: for language : String in languages where (language != "İngilizce") {
        language -> "Türkçe", "Almanca", "Fransızca"
    }


    let arr = [0,1,2,3,4,5,6,7,8,9,10]

    numberfor: for number in arr where number % 2 == 0 {
        number -> 0,2,4,6,8,10
    }


    numberfor: for i in 1...10 {
        i // -> 1,2,3,4,5,6,7,8,9,10
    }

    for i in 1..<10 {
        i // -> 1,2,3,4,5,6,7,8,9
    }

### label: for i in stride(from:to:by:) OR label: for i in stride(from:through:by:)

> 'Label' and 'where' always can be added.

    stridefor: for i in stride(from: 0, to: 9, by: 3){
       i // -> 0,3,6  // 9 is excluded
    }

    for i in stride(from: 0, through: 9, by: 3) where i % 3 == 0 {
        i // -> 0,3,6,9 // 9 is included
    }
    
### Enumerated

    let results = ["Paul", "Sophie", "Lottie", "Andrew", "John"]

    for (place, result) in results.enumerated() {
        print("\(place + 1). \(result)")
    } 
    
    
# While & Repeat While

**while (condition){    
&nbsp;&nbsp; // body  
}**  


**repeat {   
&nbsp;&nbsp; // body   
} while (condition)**  

 

    var i = 1, n = 5

    while (i<n) {
      i // -> 1,2,3,4
      i += 1
    }
    i // -> i = 5


    i = 1
    repeat {
      i += 1
      i // -> 2,3,4,5
    }while (i<n)

    i // -> 2,3,4,5


    
# Break & Continue   
    
### Break    

> **Break** is used to terminate loops or if condition. If it is used without label (generally used like this), it terminate the closest loop or if condition. It means that, whichever it is in, it breaks that one. But if it is used with a label, it can be controllable.

> **Break** terminates loops or if conditions. When the code encounter with **break**, it continue from outside of the code.

    birinciFor: for i in 1...2 {
        ikinciFor: for j in 1...5 {
            if j == 4 {
                break birinciFor
            }
            j // -> 1,2,3
        }
        i   // -> It doesn't write these. Because when j == 4, it will break the 'birincifor.'
    }

> **Continue** is used for loops. When the code encounter with **continue**, it doesn't rest of the code inside of the loop and immediatly skip that index to next one. Loop continue from next index after the code encounters with **continue**

> **Continue** can be controllable with labels like 'break'

    birinciFor: for i in 1...2 {
        ikinciFor: for j in 1...5 {
            if j == 4 {
                continue birinciFor
            }
        j // -> 1,2,3,1,2,3
        }
        i   // -> It doesn't return anything. Because every time when j == 4, it will skip this line and go to beginning of 'birincifor'
    }

