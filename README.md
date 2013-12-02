voror
=====

Voror is a daemon that watches other daemons and respawns them if a restart
file is touched. This is useful for Capistrano deployments so that restarts
require only touching a file.

## Requirements

Voror requires the **watchdog** Python module. To install it, if you're using
Pip:

```sh
pip install watchdog
```

Or if you're using easy_install:
```sh
easy_install watchdog
```

## Installing

2. Copy **./voror** into /etc/init.d/
3. Create **voror.conf** in /etc/voror/
4. Add to your startup by running ```sudo update-rc.d voror defaults```

## Configuring

Place daemons to watch on each line of your voror.conf. Example:

```
mydaemon
nginx
redis
```

## Usage

Whenever you touch ```/tmp/voror/(mydaemon|nginx|redis)```, Voror will restart
the daemon that you touched the file for.
