# MongoDB

## Steps to run MongoDB

1. `net start mongodb`
2. run /bin/mongo.exe

## Create an user

```
db.createUser({user:'your-username',pwd:'your-password',roles: [{role:'readWrite',db:'your-dbname'}]})
```

