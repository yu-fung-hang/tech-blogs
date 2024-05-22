# Nacos

## How to start Nacos

### Windows

1. Execute `./startup.cmd -m standalone` in /your-nacos-directory/bin;

2. Open http://localhost:8848/nacos/index.html on a browser, enter `nacos` as both username and password.

## Deploy the same service into two servers
1. Add the following commands into the back-up server:
```
spring.cloud.nacos.discovery.ip = ip-of-the-backup-server
spring.cloud.nacos.discovery.port = port-of-the-service
```
