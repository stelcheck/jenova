Jenova
======

Create a Docker image from a server accessible over SSH.

**Alpha release. You have been warned**

![jenova](./jenova.jpg)

Requirements
------------

* docker (and boot2docker if you are not on Linux)
* pv

Jenova doesn't currently support Windows. [PR are welcome](./issues)

Install
--------

```
sudo curl -sL https://raw.githubusercontent.com/kargo/jenova/master/jenova -o /usr/bin/jenova
```

How to use
-----------

```
jenova [ip-or-domain-name] [name-of-image-to-create] [additonal-files-or-folders-to-sync]
```

What does it do?
-----------------

1. Find the package manager on the remote host
2. Use it to find all files that were installed through it
3. Sync those files, as well as '/etc', '/opt' and '/root'
4. If you specify additional files, sync those as well

Warning
-------

### Size

Most likely the generated image will be very large (>1Gb at least). Jenova
helps you synchronizing systems, but it doesn't help you be smart. You should
use Jenova-generated images only for local development and testing purposes.

### It's Docker

To start a container from your image:

```
docker run -it [image-name] bash
```

Jenova doesn't provide replacements for `/sbin/init`. When you start a machine,
it will not start services automatically. We recommend to use
[Kargo](https://github.com/kargo/kargo) to run the generated image and
to install additional things on that image.

License
-------

[MIT](http://opensource.org/licenses/MIT).
