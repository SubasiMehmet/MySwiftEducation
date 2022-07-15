# For Loop

> **For loop can be named / labeled**

### label: for i in range/array/String where (condition)

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
    
    
# While & Repeat While

**while (condition){  **
  // body  **
}**


**repeat {  **
   // body **
 } while (condition)  **

 

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


    
    
    
    
    
