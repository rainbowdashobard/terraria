# Thanks to github.com/ryansheehan/terraria

FROM mono:4.0.5.1

MAINTAINER Christian Oelsner <c.oelsner@web.de>

RUN apt-get update && apt-get install -y zip wget \
  && apt-get clean 

ENV TSHOCK_VERSION=4.3.17 \
    SERVER_ZIP=tshock-server.zip SERVER_DIR=/opt/tshock

WORKDIR $SERVER_DIR

RUN wget https://github.com/NyxStudios/TShock/releases/download/v$TSHOCK_VERSION/tshock_release.zip -O $SERVER_ZIP

RUN unzip $SERVER_ZIP -d $SERVER_DIR \
  && rm $SERVER_ZIP \
  && chmod a+rw $SERVER_DIR/**/*

VOLUME ["/world"]

#WORKDIR $SERVER_DIR/Dedicated Server/Linux

ENTRYPOINT ["mono", "--server","--gc=sgen","-O=all","TerrariaServer.exe", "-configpath", "/world", "-worldpath", "/world", "-logpath", "/world"]

