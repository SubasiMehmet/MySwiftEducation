# NOTIFICATION CENTER

> Notification Center notifies to everywhere in the application and if there is any observer, it is notified.

--- 

### class DetailVC: UIViewController, UINavigationControllerDelegate {

> MARK: Notifying 
--- 

    NotificationCenter.default.post(name: NSNotification.Name("newData"), object: nil)

---


### class ViewController: UIViewController {
> MARK: Being Notified
--- 

    override func viewWillAppear(_ animated: Bool) {
        NotificationCenter.default.addObserver(self, selector: #selector(getData), name: NSNotification.Name("newData"), object: nil)
       
    }
    
    
> MARK: There are some system notifications. For instance, when keyboard is closed, system publish a notification. These are available on Documents.
--- 
[Notification Center.pdf](https://github.com/SubasiMehmet/MySwiftEducation/files/8886827/Notification.Center.pdf)
