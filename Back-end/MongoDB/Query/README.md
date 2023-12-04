# Query

## Fuzzy Search

### include ignore case

db.tableName.find({"fieldName":{ $regex:/XXX/ }})

e.g. {"email":{ $regex:/TER/i }}

### start with

{"email":{ $regex:/^pet/i }}