FROM debian
RUN apt-get update -y && apt-get upgrade -y && \
    apt-get install bzip2 -y

#Expose the Standard TS3 port, for files, for serverquery
EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
EXPOSE 41144

RUN useradd ts3
WORKDIR /home/t3

#Download teamspeak3 server
ADD http://dl.4players.de/ts/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2 teamspeak-server.tar.bz2

#Unpack downloaded file
RUN tar -xjvf teamspeak-server.tar.bz2
RUN rm -rf teamspeak-server.tar.bz2

WORKDIR teamspeak3-server_linux_amd64
USER ts3

ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh", "createinifile=1"]

# docker build -t averemii/ts3 .
# docker run --rm -p 9987:9987/udp -p 30033:30033 -p 10011:10011 averemii/ts3
