Redis puppet module
===================

A customised version of puppet module for redis, forked from Thomas Van Doren's version.


Usage
-----
Installs redis server and client with reasonable defaults (version 2.4.13 is included in the module).

```puppet
include redis
```

Installs redis server and client with version 2.8.3.

```puppet
class { 'redis':
  version => '2.8.3',
}
redis::instance { 'redis-default' }
```

Installs version 2.6.17, listens on default port 6379 with default settings.
Sets up 2nd instance on port 6900, binds to address 10.1.2.3 (instead of all
available interfaces), sets max memory to 1 gigabyte, and sets a password from
hiera.

```puppet
class { 'redis':
  version            => '2.6.17',
}
redis::instance { 'redis-6900':
  redis_port         => '6900',
  redis_bind_address => '10.1.2.3',
  redis_password     => hiera('redis_password'),
  redis_max_memory   => '1gb',
}
```

Authors
-------
Thomas Van Doren
Matt Ward
Ronny Haryanto

License
-------
BSD
