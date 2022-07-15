# ARRAYS

### Initializing...

    var arr1 : [Int]?
    var arr2 = [Int]()
    var arr3 = [Int](repeating: 5, count: 3) -> [3,3,3,3,3]
    

### Methods

    var arr = [0,1,2,3,4,5]

    arr.last -> 5
    arr.first -> 0
    arr.isEmpty -> false
    arr.contains(1) -> false
    arr.count -> 6
    arr.append(6) -> [0,1,2,3,4,5,6]
    arr += [7] -> [0,1,2,3,4,5,6,7]
 
 ### Insert & Remove
 
    var arr = [0,1,2,3,4,5,6,7]
    arr.insert(1, at: 15) -> 0,15,1,2,3,4,5,6,7]
    arr.remove(at: 1)   // Removes at 1 but return the removed value
    arr -> [0,1,2,3,4,5,6,7]
    arr.removeLast() -> [0,1,2,3,4,5,6]
    arr.removeFirst(2) -> [0,1,2,3,4]
    arr.removeAll() -> []
 
 ### Sort & Shuffle
 

    var arr = [6,5,4,3,2,1,0]
    var arr2 = arr.sorted() // It doesn't sort the array of 'arr'. It returns an sorted 'arr' array.
    arr.sort() -> // It sorts 'arr' array.
    
    arr.shuffle()   //Suffles the 'arr' array
    var arr4 = arr.shuffled()   //Returns suffled 'arr' array and doesn't shuffle 'arr' array.
    
    
### Random Element From Array
    
    arr.randomElement()
    
### Join
  
    var arr = [0,1,2,3,4,5]
    var str = arr7.joined(separator: "-") -> str = "0-1-2-3-4-5"
  
  
### Filter
    
    var array = [1,2,3,4,5]
    var filteredArr = array.filter{$0 < 3}
    filteredArr -> [1,2,3]

    var arrayStr = ["Hi", "Hello", "Holo"]
    var filteredStrArr = arrayStr.filter{$0.contains("lo")}
    filteredStrArr -> ["Hello", "Holo"]
    

