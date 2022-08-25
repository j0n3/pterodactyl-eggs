# pterodactyl-eggs
Eggs for Pterodactyl.io

Game servers and other services.

## Quake Live with minqlx support and plugins
This egg is based on https://github.com/parkervcp/eggs/tree/master/game_eggs/steamcmd_servers/quake_live
It's a work in progress atm, any help and suggestions for improvement are more than welcome.

### Installation
Previous to installing we need to perform some changes in pterodactyl server, assuming
that Ptereodactyl panel and Wings are installed in the same machine.

Minqlx makes use of a Redis server, and Pterodactyl host already require one
for it to work, so we will make use of it. By default, this egg uses dabase: 1 to avoid conflicts with
Pterodactyl. You can specify redis db id for the instances created with this egg.

#### Change redis config in the host
Log in into your pterodactyl server and edit /etc/redis/redis.conf

```
# Listen to any ip
bind 0.0.0.0

# Set password for the server
requirepass YOUR_REDIS_PASSWORD

# Allow connections from other hosts
protected-mode no
```

As pterodactyl panel uses this redis we also need to add the password for it.
Edit /var/www/pterodactyl/.env

and set the password
```
REDIS_PASSWORD=YOUR_REDIS_PASSWORD
```

Now you should be able to install the egg and create a server.

#### Installing the server
There are some variables added to the base QuakeLive egg (and probably more to come)
I think those are pretty self explanatory. Just follow the description and change to
your needs.

Take a look at the install script to find out which addons are available.

#### TODO
Some plugins have been added but still have to work on python dependencies and other
stuff, like adding some default workshop items for them to work. I'm working on it.
