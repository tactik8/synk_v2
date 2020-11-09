# krkn_convert

Python api to convert a record into a standardize record using a json schema as map. 

## Use case
Here is an example of use case:

A contacts record from Outlook is entered as input along with a map to convert to a standardized contact record. The api returns the standardized record. 


Input:
```
{
"first_name": "John",
"last_name": "Smith',
"contacts": {
  "email": "john@xyz.com"
  },
"employer": "xyz"
  
}
```

Map:
```
{
  "type": "object", 
  "properties": {
    "@type": {
      "const": "schema:person"
  },
  "schema:givenname": {
      "type": "string",
      "path": "first_name"
    },
  "schema:familyname": {
    "type": "string",
    "path": "last_name"
  },
   "schema:email": {
    "type": "string",
    "path": "contacts.email"
  },
  "schema:worksfor": {
    "type": "object",
    "properties": {
      "@type": {
        "const": "schema:organization"
        },
      "schema:name": {
        "type": "string",
        "path": "employer"
        }
     }
 }
```
  
  

Output:
```
{
"@type": "schema:person",
"schema:givenname": "John",
"schema:familyname": "Smith",
"schema:email": "john@wyz.com"

}
```



## Requirements
- Record schema conversion
  - Ability to map from one type of schema to another based on pre-defined map
  - Ability to generate many different type of records from one record (a contact could generate a contact record, an organization record, an address record, etc). 
- Basic field maniputlation
  - Ability to 



## input:
json: the record or list of records to convert

## output:
json list of structured records

## Description
The function accepts a string or list of string and returns a list of structured records.






