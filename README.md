# OOQ: Object-oriented Query language
  # Requirement
    #1 Implement language
      Javascript (>=ES6)
      Python     (>=3.7)
      [...]
      
    #2.Operator Overloading
      [...]
      
    #3.Multi-langguage context compiler
      var list    = [1,2,3]; //native list
      var sqlList = #query(table.filter(t=>t.id>0)); //query context
      var pyList  = #python([ a for a in list if a%2==0 ]); //python context 
      [...]
    
  # Prototype 
    #A SELECT
    #1.code: table.filter( tbl=>tbl.id > 0)
      =>sql : SELECT * FROM table WHERE table.id >0
      
    #2.code: table.filter( tbl=>tbl.id > 0).map(tbl=>["id"=>tbl.id,"full_name"=>tbl.name])
      =>sql : SELECT table.id AS id,table.name AS full_name FROM table WHERE table.id >0
      
    #3.code: table.filter( tbl=>tbl.id > 0).map(tbl=>tbl.id)
      =>sql : SELECT table.id FROM table WHERE table.id >0

    #4.code: table.filter( tbl=>tbl.id > 0).map(tbl=>tbl.id).sort(tbl=>tbl.id)
      =>sql : SELECT table.id  FROM table WHERE table.id >0 ORDER BY tbl.id ASC
      
    #5.code: table.filter( tbl=>tbl.id > 0).map(tbl=>tbl.id).sort(tbl=>-tbl.id)
      =>sql : SELECT table.id FROM table WHERE table.id >0 ORDER BY tbl.id DESC
      
    #6.code: table.filter( tbl=>tbl.id > 0).slice(1,3)
      =>sql : SELECT table.id FROM table WHERE table.id >0 LIMIT 1,3
      
    #7.code: table.filter( tbl=>tbl.id > 0).join(table2,tbls=>tbls[0].refId=tbls[1].id)
      =>sql : SELECT * FROM table JOIN table2 ON table.refId = table2.id WHERE table.id >0 LIMIT 1,3 
      [...]
    
  # Features
      [...]
