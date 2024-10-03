# Linux Commands

## Scenario 1: tar a tar.gz file
```
tar -zxvf filename.tar.gz
```

## Scenario 2: grant permission to a folder
```
chmod -R 777 your-folder-name
```

## Scenario 3: kill a process
```
netstat -tunlp | grep your-port-number
kill -9 processId
```

## Scenario 4: list all Java processes
```
ps -ef | grep java
```

`ps`: process status

`-e`: show all processes

`-f`: show processes in full format

`grep`: global regular expression print (globally search for a regular expression and print matching lines)

`java`: Java processes only

## Scenario 5: run a command even after you log out

When you execute a Unix job in the background, and log out from the session, your process will get killed.

`nohup` (no hang up) frees you from connecting to the shell and waiting for the command to complete.

Example:
```
nohup java -jar ./your-jar-name.jar --server.port=your-port &
```

## Scenario 6: read a .out file

* Execute `tail -f filename.out` if you want to read the live data;

* Execute `tail -n 500 filename.out` if you want to read the last 500 lines of the .out file.

## Scenario 7: open firewall ports

* Check whether a port has been opened: `firewall-cmd --query-port=9200/tcp`;

* Execute `sudo firewall-cmd --add-port=8056/tcp --permanent` if you want to open a firewall port;

* Execute `firewall-cmd --permanent --add-port 60000-61000/tcp` if you want to open a range of ports.

Don't forget to reload the firewall: `sudo firewall-cmd --reload`

## Scenario 8: access another server in a server

```
ssh target-username@target-server-host
```