---
title: "Data on the Web"
teaching: 15
exercises: 0
questions:
- "How do I read data types like JSON & XML?"
objectives:
- "Understand commmon types of structured data"
- "Understand concepts realted to APIs"
keypoints:
- "How to read structured data types: JSON & XML"
- "What are parameters?"
- "What are appropriate uses of data retrieved via API?"
---

## Data Formats

- **JSON** – JavaScript Object Notation
  - Plain text, can open n any text editor or web browser
- **XML** – eXtensible Markup Language


## Concepts

- **Params** – Parameters
    - _The variables that specify how your requests are handled_
       - _Search Parameters_
- **Key/Value pairs**
    - _A unique identifier (key) for a category of data and the actual data (value) for that_
       _category_
```
{
 “key1”: “value”,
 “key2”: 170
 “key2”: [ “value1”, “value2” ],
 “key3”: {
    “key3.1”: “value”,
    “key3.2”: “value”
}
          }
```

### JSON
- Many types of data can be stored in JSON

```
{
"firstName" : "John",
"lastName" : "Smith",
"isAlive" : true ,
"age" : 25 ,
"address" : {
"streetAddress" : "21 2nd Street",
"city" : "New York",
"state" : "NY",
"postalCode" : "10021"
},
"phoneNumbers" : [
{
"type" : "home",
"number" : "212 555-1234"
},
{
"type" : "office",
"number" : "646 555-4567"
},
{
"type" : "mobile",
"number" : "123 456-7890"
}
],
"children" : [],
"spouse" : null
}
```

Here's the same data with the Key/Value pairs labled:

![Sample JSON data](../assets/img/Slide06.png)

### XML

## Appropriate Use