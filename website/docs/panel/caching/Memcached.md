---
sidebar_position: 3
---

# Memcached

![memcached_disabled.png](/img/panel/v2/memcmain.png)

Memcached is a high-performance, distributed memory caching system. It is often used to speed up dynamic database-driven websites and applications by caching data in memory.

It is commonly used to reduce the load on a database server and improve the responsiveness of websites by caching frequently accessed data, such as database query results or API responses.

## Enable / Disable

You have the options to enable or disable the Memcached service as needed. Disabling it will promptly clear all existing Memcached data from memory.

Enabling the Memcached service will start the service using the default Memcached port, which is _11211_.

![memcached_enabled.png](/img/panel/v2/memcenabled.png)

## Set Memory Limits

Upon initialization the Memcached container has default memory limits set, it is advisable to set memory limits appropriate to your use case and needs.

You can set these limits on the /containers interface which is accessible through the user panel navigation on Docker/containers .

:::info
Changing the memory limit will necessitate the service to restart to apply the new restrictions, resulting in the removal of all existing cache data.
:::

![memcached_limits.png](/img/panel/v2/memclimits.png)

## Connect to Memcached

To establish a connection to your Memcached instance, use the following details:

- Server address: **memcached** (not 127.0.0.1)
- Port: **11211** (the default Memcached port)

For testing the connection to the Memcached server, you can use the following tools or scripts.

### Test Connection with PHP

1. Navigate to your website directory using a File Manager.
2. Create a new file named _memcached-test.php_.
3. Add the following PHP code to the newly created file and save it:

```php
<?php 
   // Connect to Memcached server on localhost 
   $memcached = new Memcached(); 
   $memcached->addServer('memcached', 11211); 
   echo "Connection to server successful"; 
   // Check whether the server is running or not 
   echo "Server is running: ".$memcached->getVersion(); 
?>
```

Access your website in a browser and append /memcached-test.php. For example, if your website is example.com, you should open example.com/memcached-test.php

You should see the "Server is running.." message, indicating that the Memcached service is active, and the connection is established.


### WordPress Plugins

To implement Memcached caching for your WordPress website, you'll need a dedicated plugin. Here are some WordPress plugins we've tested for Memcached caching:

- [Memcached Object Cache](https://wordpress.org/plugins/memcached/)

## View Logs

You have the option to access the Memcached service logs. By doing so, you can identify any service errors or check for memory usage and limits.

![memcached_log.png](/img/panel/v2/memclogs.png)

