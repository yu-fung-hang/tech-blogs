# Execute a Jar file and handle .out properly

```Shell
#!/bin/bash

SVR=your-jar-file-prefix
echo $SVR

TARGET=`ls -t|grep $SVR|grep jar|awk 'NR == 1'`
echo 'The target jar file is: '$TARGET

PID=`ps x|grep $SVR|grep jar|awk '{print $1}'`
echo 'The target PID is: '$PID
kill -9 $PID

EXECDATE=$(date +'%Y%m%d')
echo 'The date string is:'$EXECDATE

if [ ! -f $SVR.out ]; then
        touch $SVR.out
fi

cp $SVR.out $SVR.out_$EXECDATE
cat /dev/null>$SVR.out
nohup java -Xmx1024m -Xms512m -jar -Dfile.encoding=UTF-8 -Dserver.port=your-port $TARGET 2>&1 </dev/null |cat >> $SVR.out &
tail -n500 $SVR.out
```