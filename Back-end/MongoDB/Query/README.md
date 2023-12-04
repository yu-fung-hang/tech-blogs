# Query

## Fuzzy Search

db.tableName.find({"fieldName":{ $regex:/XXX/ }})

e.g. {"email":{ $regex:/TER/i }}