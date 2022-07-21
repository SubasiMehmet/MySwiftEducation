# Picker


class DetailsVC: UIViewController, UIImagePickerControllerDelegate, UINavigationControllerDelegate {

**Open Picker**

    @objc func selectImage() {                  
        let picker = UIImagePickerController()  
        picker.delegate = self
        picker.sourceType = .photoLibrary
        picker.allowsEditing = true             
        present(picker, animated: true, completion: nil)
        
    }
    
**Did Finish Picking**

    func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [UIImagePickerController.InfoKey : Any]) {
        ImageView.image = info[.editedImage] as? UIImage
        SaveButton.isEnabled = true
        self.dismiss(animated: true, completion: nil)  //picker'ı kapatmak için
    }


