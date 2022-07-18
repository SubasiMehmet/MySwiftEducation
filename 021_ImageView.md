# ImageView()

---

### Example 

    var images = [UIImageView]()  -> Array
    var tableImage = UIImageView()
    
> Initialize the images array    

    for _ in 0...6 {   
        let image = UIImageView()
        images.append(image)
    }
    
    
> Assing images and some other specialities

     for (index, _) in picturesNames.enumerated() {
        images[index].image = UIImage(named: "\(picturesNames[index])")
        images[index].translatesAutoresizingMaskIntoConstraints = false
        images[index].contentMode = .scaleAspectFit
            
         if index > 0 {
            images[index].isHidden = true
         }
         view.addSubview(images[index])
      }
      
      images[5].layer.zPosition = -1000. -> Default is 0. 1 is frontside according to 0.
      
---
