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