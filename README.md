voror
=====

Voror is a daemon that watches other daemons and respawns them if a restart
file is touched. This is useful for Capistrano deployments so that restarts
require only touching a file.

## Installing

1. Copy **./daemon/voror** into /etc/init.d/
2. Copy **./voror** into /etc/voror/
3. Create **voror.conf** in /etc/voror/
4. Add to your startup by running ```sh update-rc.d voror defaults```

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
