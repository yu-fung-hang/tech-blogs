# Install MySQL

1. Pull MySQL 5.7 image:
```
docker pull mysql:5.7
```

2. Execute the following command to start MySQL:
```
docker run -d -p 3306:3306 --privileged=true -v /your-directory/mysql5.7/log:/var/log/mysql -v /your-directory/mysql5.7/data:/var/lib/mysql -v /your-directory/mysql5.7/conf:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=your-password --name mysql mysql:5.7
```
In my case it would be:
```
docker run -d -p 3306:3306 --privileged=true -v /software/mysql5.7/log:/var/log/mysql -v /software/mysql5.7/data:/var/lib/mysql -v /software/mysql5.7/conf:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=1234qwer --name mysql mysql:5.7
```

3. Go to your conf directory, create a file named `my.cnf`. In my case:
```
cd /software/mysql5.7/conf
gedit my.cnf
```

Paste the following content into `my.cnf` to modify MySQL's character encoding:
```
[client]
default_character_set=utf8
[mysqld]
collation_server = utf8_general_ci
character_set_server = utf8
```

4. Restart MySQL
```
docker restart mysql
```