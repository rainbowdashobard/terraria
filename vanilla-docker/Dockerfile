FROM ubuntu:14.04.4

MAINTAINER Christian Oelsner <c.oelsner@web.de>

# Add mono repository
# Update and install mono and a zip utility
# fix for favorites.json error
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF \
  && echo "deb http://download.mono-project.com/repo/debian wheezy/snapshots/4.0.5.1 main" | sudo tee /etc/apt/sources.list.d/mono-xamarin.list

RUN apt-get update && apt-get install -y zip wget mono-complete \
  && apt-get clean \
  && favorites_path="/root/My Games/Terraria" \
  && mkdir -p "$favorites_path" \
  && echo "{}" > "$favorites_path/favorites.json"

ENV SERVER_VERSION=133 SERVER_ZIP=terraria-server.zip SERVER_DIR=/opt/terraria

WORKDIR $SERVER_DIR

RUN wget http://terraria.org/server/terraria-server-$SERVER_VERSION.zip -O $SERVER_ZIP

RUN unzip $SERVER_ZIP -d $SERVER_DIR \
  && rm $SERVER_ZIP \
  && chmod a+rw $SERVER_DIR/**/*

VOLUME ["/world"]

WORKDIR $SERVER_DIR/Dedicated Server/Linux

ENTRYPOINT ["mono", "--server","--gc=sgen","-O=all","TerrariaServer.exe", "-configpath", "/world", "-worldpath", "/world", "-logpath", "/world"]

