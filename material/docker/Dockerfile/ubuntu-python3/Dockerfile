# Executar o Dockerfile
# NOTA: o "ponto final" faz parte do comando
#
# docker build -f <NOME DA IMAGEM> .
#

# Instala o Ubuntu
FROM ubuntu
# FROM node:alpine

# Atualiza e baixa programas
RUN apt-get -y update
RUN apt-get -y install python3

# Expoe uma porta com o protocolo
EXPOSE 80/tcp
EXPOSE 80/udp

# Cria um usuario
RUN adduser -h /home/convidado -s /bin/bash -D convidado

# Seleciona o usuario
USER convidado
RUN whoami

# Define ambiente de trabalho
WORKDIR /usr/src/principal

