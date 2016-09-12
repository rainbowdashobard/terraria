FROM mono:4.0.5.1

MAINTAINER Christian Oelsner <c.oelsner@web.de>

RUN apt-get update && apt-get install -y zip wget \
  && apt-get clean 

ENV SERVER_VERSION=1331 SERVER_ZIP=terraria-server.zip SERVER_DIR=/opt/terraria

WORKDIR $SERVER_DIR

RUN wget http://terraria.org/server/terraria-server-$SERVER_VERSION.zip -O $SERVER_ZIP

RUN unzip $SERVER_ZIP -d $SERVER_DIR \
  && rm $SERVER_ZIP \
  && chmod a+rw $SERVER_DIR/**/*

VOLUME ["/world"]

WORKDIR $SERVER_DIR/Dedicated Server/Linux

ENTRYPOINT ["mono", "--server","--gc=sgen","-O=all","TerrariaServer.exe", "-configpath", "/world", "-worldpath", "/world", "-logpath", "/world"]

