# JSON

## 1

> Creating JSON URL

**ViewController**

    override func viewDidLoad() {
        let urlString: String
        
            urlString = "https://www.hackingwithswift.com/samples/petitions-1.json"
        
        if let url = URL(string: urlString) {
            if let data = try? Data(contentsOf: url){
                parse(json: data)
            }
        }else{
            showError()
         }
     }
     
    func parse(json: Data) {
        let decoder = JSONDecoder()
        
        if let jsonPetitions = try? decoder.decode(Petitions.self, from: json){
            petitions = jsonPetitions.results
            tableView.reloadData()
        }
    }
    
     
---

> **Attributes**

**Petition.switf**

    struct Petition: Codable{
        var title: String
        var body: String
        var signatureCount: Int
    }
   
> This variables' names must be same with JSON's variables's names, exactly!!!


---

> **Result**

**Petitions.swift**

> String of 'results' need to be same in json page!!!

    struct Petitions: Codable {
        var results: [Petition]
    }
    
> This cluster name must be same with variables' cluster's name of JSON!!!

## 2

**1. Request & Session**

**2. Response & Data**

**3. Parsing & JSON Serialization**
        
> 1. Request & Session

    let url = URL(string: "http://data.fixer.io/api/latest?access_key=557cb129f1d94a831bdd7dfaee7d62ea")
        
    let session = URLSession.shared
    
    
        //Closure
        let task = session.dataTask(with: url!) { (data, response, error) in
            if error != nil {
                Alert(title: "Error", message: error?.localizedDescription)
            }
            
            else{
                
> 2. Response & Data
                if data != nil {
                    
                    do {
                        let jsonResponse = try JSONSerialization.jsonObject(with: data!, options: JSONSerialization.ReadingOptions.mutableContainers) as! Dictionary <String, Any>
                        
                        
> 3. Parsing & JSON Serialization

                        DispatchQueue.main.async {
                            if let rates = jsonResponse["rates"] as? Dictionary <String, Double> { // as? [String, Double]
                                //print(rates)
                                if let cad = rates["CAD"] {
                                    self.CADLabel.text = "CAD: \(cad)"
                                }
                                if let usd = rates["USD"] {
                                    self.USDLabel.text = "USD: \(usd)"
                                }
                                if let try_lira = rates["TRY"] {
                                    self.TRYLabel.text = "TRY: \(try_lira)"
                                }
                                
                                
                            }
                        }
                    }catch{
                        print("Error")
                    }
                }
                
            }
        }
        
        task.resume()
        

> //ASYNC This process is async because these fetching processes need to be proceeded in background. Otherwise, it might lock the app.

> Don't forget **task.resume!!**
