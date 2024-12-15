# JDK

## Install JDK 17 on Linux

```
cd /opt/module
wget https://download.java.net/java/GA/jdk17.0.2/dfd4a8d0985749f896bed50d7138ee7f/8/GPL/openjdk-17.0.2_linux-x64_bin.tar.gz
tar zxf openjdk-17.0.2_linux-x64_bin.tar.gz

vim /etc/profile

export JAVA_HOME=/opt/module/jdk-17.0.2/
export CLASSPATH=$JAVA_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$PATH

source /etc/profile

java -version
```