import ChangeLog from '../changelog/connector-rabbitmq.md';

# Rabbitmq

> Rabbitmq sink connector

## Description

Used to write data to Rabbitmq.

## Key features

- [ ] [exactly-once](../../concept/connector-v2-features.md)

## Options

|            name            |  type   | required | default value |
|----------------------------|---------|----------|---------------|
| host                       | string  | yes      | -             |
| port                       | int     | yes      | -             |
| virtual_host               | string  | yes      | -             |
| username                   | string  | yes      | -             |
| password                   | string  | yes      | -             |
| queue_name                 | string  | yes      | -             |
| durable                    | boolean | yes      | -             |
| exclusive                  | boolean | yes      | -             |
| auto_delete                | boolean | yes      | -             |
| url                        | string  | no       | -             |
| network_recovery_interval  | int     | no       | -             |
| topology_recovery_enabled  | boolean | no       | -             |
| automatic_recovery_enabled | boolean | no       | -             |
| use_correlation_id         | boolean | no       | false         |
| connection_timeout         | int     | no       | -             |
| rabbitmq.config            | map     | no       | -             |
| common-options             |         | no       | -             |

### host [string]

the default host to use for connections

### port [int]

the default port to use for connections

### virtual_host [string]

virtual host – the virtual host to use when connecting to the broker

### username [string]

the AMQP user name to use when connecting to the broker

### password [string]

the password to use when connecting to the broker

### url [string]

convenience method for setting the fields in an AMQP URI: host, port, username, password and virtual host

### queue_name [string]

the queue to write the message to

### durable [boolean]

true: The queue will survive a server restart.
false: The queue will be deleted on server restart.

### exclusive [boolean]

true: The queue is used only by the current connection and will be deleted when the connection closes.
false: The queue can be used by multiple connections.

### auto_delete [boolean]

true: The queue will be deleted automatically when the last consumer unsubscribes.
false: The queue will not be automatically deleted.

### schema [Config]

#### fields [Config]

the schema fields of upstream data.

### network_recovery_interval [int]

how long will automatic recovery wait before attempting to reconnect, in ms

### topology_recovery_enabled [boolean]

if true, enables topology recovery

### automatic_recovery_enabled [boolean]

if true, enables connection recovery

### use_correlation_id [boolean]

whether the messages received are supplied with a unique id to deduplicate messages (in case of failed acknowledgments).

### connection_timeout [int]

connection TCP establishment timeout in milliseconds; zero for infinite

### rabbitmq.config [map]

In addition to the above parameters that must be specified by the RabbitMQ client, the user can also specify multiple non-mandatory parameters for the client, covering [all the parameters specified in the official RabbitMQ document](https://www.rabbitmq.com/configure.html).

### common options

Sink plugin common parameters, please refer to [Sink Common Options](../sink-common-options.md) for details

## Example

simple:

```hocon
sink {
      RabbitMQ {
          host = "rabbitmq-e2e"
          port = 5672
          virtual_host = "/"
          username = "guest"
          password = "guest"
          queue_name = "test1"
          rabbitmq.config = {
            requested-heartbeat = 10
            connection-timeout = 10
          }
      }
}
```

### Example 2

queue with durable, exclusive, auto_delete:

```hocon
sink {
      RabbitMQ {
          host = "rabbitmq-e2e"
          port = 5672
          virtual_host = "/"
          username = "guest"
          password = "guest"
          queue_name = "test1"
          durable = "true"
          exclusive = "false"
          auto_delete = "false"
          rabbitmq.config = {
            requested-heartbeat = 10
            connection-timeout = 10
          }
      }
}
```

## Changelog

<ChangeLog />

