FROM debian

MAINTAINER mnidokin <mnidokin@student.21-school.ru>

RUN apt-get update && \
	apt-get upgrade -y && \
	apt-get install -y wget default-jre

WORKDIR minecraft

RUN https://launcher.mojang.com/v1/objects/4d1826eebac84847c71a77f9349cc22afd0cf0a1/server.jar

RUN echo 'eula=true' > eula.txt

EXPOSE 25565

ENTRYPOINT java -Xmx1024M -Xms1024M -jar server.jar
