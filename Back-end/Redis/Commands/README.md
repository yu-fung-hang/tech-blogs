# Redis Commands

## Scenario 1: Set password

No password is required to sign in Redis by default. It is necessary to set one to ensure security.

1. Modify `/your-redis-directory/redis.windows.conf`: remove `#` in `#requirepass foobared` and replace your new password with `foobared`.

2. Open CMD, `cd your-redis-directory` and execute the following command:
```
redis-server.exe redis.windows.conf
```