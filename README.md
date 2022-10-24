# GraphQL
## Install dependencies:
```npm init```

```npm i express express-graphql graphql nodemon```

```npm i --save-dev @babel/cli @babel/core @babel/node @babel/preset-env```
 
## Add persistence:
  - Mongoldb.com
  - Follow the mongodb instructions
  - Install Robo 3T (mongodb connection manager)
  - Create file dbConnectors.js
  - Install dependencies: 
  
  ```npm i mongoose sequelize sqlite3 casual lodash```
## GraphiQL:
## Mutations
 
 ```
 mutation {
  createProduct(input: {
    name: "Widget from GraphiQL",
    description: "W GraphiQL description",
    price: 5.55,
    soldout: ONSALE,
    stores: [
      { store: "Store GraphiQL_1" },
      { store: "Store GraphiQL_2" },
    ],   
  }){
    	id
    	name
    	description
    	price
    	soldout
	stores { store }
  }
}
```
```
mutation{
  updateProduct(input: {
    id: "63503390e64c4275d335745a"
    name: "updated name"
    description: "updated description",
    soldout: ONSALE
    inventory: 44
    stores:[
      {
        store: "New store"
      }
    ]
   
  }){
    name
    description
  }
}
```
```
mutation{
  deleteProduct(id: "63501d25f45108c7fd908324")
}
```
## Queries
```
query{
  getProduct(id: "63501d25f45108c7fd908324"){
    	id
    	name
    	description
    	price
   	soldout
  }
}
```
```
query{
  getAllProducts{
    name
    price
    description
  }
}
```

## Query with aliases
- Add labels to query:
```
query{
  
  DescriptionLabel: getProduct(id: "63503390e64c4275d335745a"){
    price
    description
  }
  
  SomeLabel: getProduct(id: "6350322af45108c7fd908327"){
    name
    description
  }
}
```

- Query with fragment
```
query{
  
  Widget_1: getProduct(id: "63503390e64c4275d335745a"){
		...widgetFragment
  }
  
  Widget_2: getProduct(id: "6350322af45108c7fd908327"){
		...widgetFragment
  }
}

fragment widgetFragment on Product{
  name
  price
  description
  soldout
}
```
  
## Mongodb
<img width="1268" alt="image" src="https://user-images.githubusercontent.com/45378000/196783089-505b3c1f-35e0-4012-9f77-a392c3b7d373.png">
