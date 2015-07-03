# Using Subdomains in Development

In order to use subdomains, like for handling
api requests you need to setup some configuration.

On macs there is a file /etc/hosts that associates
ip addresses and domain names.

For example:
```
127.0.0.1 localhost
```

One commen convention is to use the name of the domain
in production with a -dev.com at the end.

For example if your production domain was cars.com; your development environment
could use:
```
#/etc/hosts
127.0.0.1 cars-dev.com
```

To use an api subdomain add:
```
#/etc/hosts
127.0.0.1 cars-dev.com
127.0.0.1 api.cs-zombies-dev.com
```

Some alternative solutions include:
[Pow](http://pow.cx)
[LVH.me](http://lvh.me)
