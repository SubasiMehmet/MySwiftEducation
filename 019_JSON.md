# JSON

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
   
> This variables' names must be same with JSON's variables's names, exactly.


---

> **Result**

**Petitions.swift**

//MARK: - String of 'results' need to be same in json page

    struct Petitions: Codable {
        var results: [Petition]
    }
    
> This cluster name must be same with variables' cluster's nam of JSON.
