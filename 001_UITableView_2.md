# UITABLEVIEW()
### tableView.dequeueReusableCell(withIdentifier: "Picture", for: indexPath)

> If protoype cell is created with StoryBoard, cell need to have a identifier.


![Screen Shot 2022-06-19 at 23 45 44](https://user-images.githubusercontent.com/50085545/174499805-0251f36a-d3ef-482f-b0a6-9bf6572dc33d.png)


---


> MARK: With this identifier, the cell is put to function.



    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "Picture", for: indexPath)
        cell.textLabel?.text = pictures[indexPath.row]
        //MARK: Change the font of the textLabel
        // cell.textLabel?.font = .systemFont(ofSize: 20)
        return cell
    }
    
    
> MARK:With this function, it is defined that which cell is returned in which row. Different prototype cells is returned in different rows.


--- 
> MARK: Everycell has a text label as default. Thanks to this, text can be added and shown directly.

    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = ...
        cell.textLabel?.text = pictures[indexPath.row]
        cell.textLabel?.font = .systemFont(ofSize: 20)
        return cell
    }
