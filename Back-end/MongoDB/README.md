# MongoDB

## Steps to run MongoDB

1. Run cmd as Administrator, execute:
    1. `net start mongodb`
    2. `mongo`
2. If you want to stop the service, execute `net stop mongodb` in a new cmd (Administrator).

## Steps to enable authentication

1. Run cmd as Administrator, start MongoDB:
    1. execute `net start mongodb`;
    2. execute `mongo`. 
2. Use `admin` database and create a root user:
    1. execute `use admin`;
    2. execute `db.createUser({user:'root',pwd:'1234qwer',roles:[{role:'root',db:'admin'}]})`.
3. Close the current cmd and open a new one. Restart MongoDB by executing the following:
    1. `net stop mongodb`;
    2. `net start mongodb`.
4. In cmd go to `your-mongodb-directory/bin`, execute `mongod --auth` to enable authentication.
5. Enter `mongo`, then enter `use admin` to switch to `admin` database.
6. Enter `db.auth('root', '1234qwer')` to authenticate. It means success if it returns 1.
7. Create a new user in your database:
    1. `use your-database-name`
    2. `db.createUser({user:'your-username',pwd:'your-password',roles:[{role:'readWrite',db:'your-database-name'}]})`
8. Log in MongoDB with this user:`mongo 127.0.0.1/your-database-name -u your-username -p`

### Drop a user:
```
db.dropUser('your-username')
```
### Get all the rows of a collection (table)
```
db.your-collection-name.find().pretty()
```
Example: db.location.find().pretty()