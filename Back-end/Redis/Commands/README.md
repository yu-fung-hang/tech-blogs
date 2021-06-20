# Redis Commands

## Scenario 1: Set password

No password is required to sign in Redis by default. It is necessary to set one to ensure security.

1. Modify `/your-redis-directory/redis.windows.conf`: remove `#` in `#requirepass foobared` and replace `foobared` with your new password.

2. Open CMD, `cd your-redis-directory` and execute the following command:
```
redis-server.exe redis.windows.conf
```

3. Access redis-cli.exe with password:
```
auth your-password
```