# How to set-up multiple servers

Open AccontServer.ini

```
AddTail( -1, 1, "FlyFF", "127.0.0.1", 0, 1, 0, 1 );
	AddTail( 1, 1, "Channel 1", "127.0.0.1", 1, 1, 500, 1 );
```

Look at the two first numbers:
- If the first number is -1, it means it is a server (orange part on [the graph](README.md)).
  - The second number is the Sys id of the server.
- If the first number is not -1, it is the Sys id of the server and this is a channel
  - Second number if the channel id. It must be `> 0` and `< 100`.

The key of a channel is `Sys * 100 + channel id`. All channel keys must be unique.

## Multiple channels

1/ Add a new line for your new channel, for example:

```
	AddTail( 1, 2, "Channel 2", "127.0.0.1", 1, 1, 500, 1 );
```

2/ Edit your `CoreServer.ini` to add all worlds to your new channel.

CoreServer.ini lists the maps for each channel by their key. Just give
all existing maps to each channel.

3/ Copy WorldServer.exe and WorldServer.ini in another folder, modify
the key in the `WorldServer.ini` file.


## Multiple servers

### The intended way: one server on its own machine

It is intended that each server is on its own machine.


### The hacky way: changing the code so one machine can support multiple servers

***TODO***


