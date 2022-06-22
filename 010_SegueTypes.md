# SEGUE TYPES


### Show & Present Modally


> Show and Present Modally can be used interchangeably by determining the presentation style with storyboard, code or segue settings.




### Popover

> Popover is valid for iPads. On phone, it works standard "show segue."



### Custom

> A segue can be defined with code.

    let mainSB = UIStoryboard(name: "Main", bundle: Bundle.main)
    let customVC = mainSB.instantiateViewController(withIdentifier: "customVC")      

    customVC.modalPresentationStyle = .fullScreen //or .overFullScreen for transparency
    present(customVC, animated: true)

---    
> Other ways

    show(customVC, sender: nil)       

> MARK: In this method, because storyboard is optional, we have use typecasting.

    let customVC = storyboard?.instantiateViewController(withIdentifier: "customVC") as? CustomVC
            
> MARK: MARK: There is no navigationController

    navigationController?.pushViewController(customVC, animated: true)
