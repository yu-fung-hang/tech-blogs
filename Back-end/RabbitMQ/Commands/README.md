# RabbitMQ Commands

## Restart RabbitMQ on Windows
```
net stop rabbitmq
net start rabbitmq
```

## Install rabbitmq-delayed-message-exchange
1. Download a `.ez` file from https://github.com/rabbitmq/rabbitmq-delayed-message-exchange/releases;
2. Put the `.ez` file into /your-rabbitmq-directory/plugins;
3. Execute `rabbitmq-plugins enable rabbitmq_delayed_message_exchange` on `cmd`;
4. Restart RabbitMQ;
5. Go to http://localhost:15672/#/, and try to add a new exchange.