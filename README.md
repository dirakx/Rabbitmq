After installation you must begin the server with init.d/rabbit..server start

## Restart rabbit

* sudo rabbitmqctl stop_app
* sudo rabbitmqctlforce_reset
* sudo rabbitmqctl start_app
* sudo rabbitmqctl list_queues

## Create an adminsitrator user

* sudo rabbitmqctl add_user zinalat zinalat  
* sudo rabbitmqctl set_user_tags zinalat  administrator

## Create a vhost
* sudo rabbitmqctl add_vhost /
* sudo rabbitmqctl list_vhosts

## Enable plugins

* sudo rabbitmq-plugins enable --offline  webmachine

## Management console
* rabbitmq-plugins enable rabbitmq_management
* localhost:15672
* localhost:15672/cli

## Adding user to a vhost
* A new created user should be added as access to a vhost this can be done via the admin
of the management console.
* or  sudo rabbitmqctl set_permissions -p myvhost myuser  ".*" ".*" ".*"

## Finding the number of workers currently consuming from a queue:

$ rabbitmqctl list_queues name consumers

## Finding the amount of memory allocated to a queue:

$ rabbitmqctl list_queues name memory

## Having 2 celery in the same machine

When having 2 celery in the same machine, make two different vhost 

## Reboot the machine

When reboot the machine will change the hostname, re-set it and then kill all the rabbit process, then re-init rabbit. 

## Purge queues

* Via admin

## config 
The ip is the internal ip of the VM.

[
  {rabbit, [
    {tcp_listeners, [{"127.0.0.1", 5672},
                     {"::1",       5672},
                     {"10.249.30.196",   5672}
]}
  ]}
].

# Set RAM usage threshold
sudo rabbitmqctl set_vm_memory_high_watermark 0.6    (o.6 = 60%)

## TODOS
if a node fails, take a look at how to restart it, also you can restart the rabbit server with
* sudo /etc/init.d/rabbitmq-server start  but only when you NEED to do it, otherwise is better to use stop_app and start_aop


## References
* [[Rabbit]]
* http://www.rabbitmq.com/man/rabbitmqctl.1.man.html
* http://www.rabbitmq.com/management.html
* http://stackoverflow.com/questions/8737754/node-with-name-rabbit-already-running-but-also-unable-to-connect-to-node
