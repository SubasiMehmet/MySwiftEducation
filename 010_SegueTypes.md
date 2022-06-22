# SEGUE TYPES


### Show & Present Modally


> Show and Present Modally can be used interchangeably by determining the presentation style with storyboard, code or segue settings.

![Screen Shot 2022-06-22 at 06 37 57](https://user-images.githubusercontent.com/50085545/174939250-22387b18-2724-4365-a37b-748cb9d24226.png)

![Screen Shot 2022-06-22 at 06 38 39](https://user-images.githubusercontent.com/50085545/174939277-fc7b7c23-5e5b-4907-ada9-dd7aed3dc6a3.png)


### Popover

> Popover is valid for iPads. On phone, it works standard "show segue."

![Screen Shot 2022-06-22 at 06 40 24](https://user-images.githubusercontent.com/50085545/174939236-18b11e94-8d47-4519-b543-931990753768.png)


### Custom

> A segue can be defined with code.

    let mainStoryBoard = UIStoryboard(name: "Main", bundle: Bundle.main)
    let customVC = mainStoryBoard.instantiateViewController(withIdentifier: "customVC")      

    customVC.modalPresentationStyle = .fullScreen //or .overFullScreen for transparency
    present(customVC, animated: true)

---    
> Other ways

    show(customVC, sender: nil)       

> MARK: In this method, because storyboard is optional, we have use typecasting.

    let customVC = storyboard?.instantiateViewController(withIdentifier: "customVC") as? CustomVC
            
> MARK: MARK: There is no navigationController

    navigationController?.pushViewController(customVC, animated: true)
