# Terraria related stuff
A mixture of terraria related files ...

## Vanill Dedicated Server
The Dockerfile within `vanilla-docker` containerizes a vanilla dedicated terraria server. Due to the shipped mono runtime by terraria itself, it isn't necessary to install mono-complete.

Starting a dedicated server in interactive mode:

    docker run -it -p 7777:7777 -v $HOME/terraria/world:/world --name="terraria" coelsner/terraria:vanilla-latest

Shoutout to [Ryan Sheehan](https://github.com/ryansheehan) for providing a dockerized server with TShock: [ryshe/terraria](https://hub.docker.com/r/ryshe/terraria/)
