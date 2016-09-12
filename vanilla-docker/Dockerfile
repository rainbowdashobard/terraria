FROM ubuntu:14.04

MAINTAINER Christian Oelsner <c.oelsner@web.de>

RUN apt-get update && apt-get install -y zip wget \
  && apt-get clean 

ENV SERVER_VERSION=1331 SERVER_ZIP=terraria-server.zip SERVER_DIR=/opt/terraria

WORKDIR $SERVER_DIR

RUN wget http://terraria.org/server/terraria-server-$SERVER_VERSION.zip -O $SERVER_ZIP \
  && unzip $SERVER_ZIP 'Dedicated Server/Linux/*' -d $SERVER_DIR \ 
  && rm $SERVER_ZIP \
  && cd ./Dedicated\ Server/Linux \
  && chmod a+rw * \
  && chmod a+x TerrariaServer*

VOLUME ["/world"]

WORKDIR $SERVER_DIR/Dedicated Server/Linux

ENTRYPOINT ["./TerrariaServer", "-x64", "-configpath", "/world", "-worldpath", "/world", "-logpath", "/world"]

