# Plex no Docker

Este repositorio cria um servidor de streaming usando o Plex Media Server.

## Requerimentos

Instalar Docker.

## Local das midias

No arquivo '.env' estão declaradas variaveis que apontam para diretorios de midia.
Este servidor conta com 2 HDs e portando, precisa de duas variaveis.

O arquivo `.env` possui uma estrutura similar a que esta abaixo.
```
# caminho dos arquivos de midia e do servidor
MEDIA_Lenny=/media/edson/ANDROID-Lenny/
MEDIA_Famous=/media/edson/ANDROID-Famous/
```
Onde as variaveis são colocadas uma por linha e dividida por um sinal de igual(=), que separa o nome da variavel a esquerda e seu valor. Neste caso, o caminho do dispositivo de armazenamento.
A primeira linha é um comentario.
A segunda e terceira declaram os caminhos do armazenamento.
Lembre-se que ao modificar algum valor em `.env` é necessario verificar o arquivo `plex.yalm`.

## Como rodar o Plex?

Execute o comando abaixo no terminal:

`docker-compose up -d`

Use o link [localhost:32400/manege](http://localhost:32400/manege) para acessar o Plex.

## IMPORTANTE

Se esta tendo travamentos e pausas no streaming de midia, pra corrigir isso devemos dizer ao Plex, que nao fazer o transcode pra poupar largura de banda, entao devemos configurar os Clientes Plex (sim, devemos fazer isso em cada Cliente) para que reproduza a midia na qualidade maxima (sem fazer transcode). No Android e iPhone, as configurações são muito similares, veja a screenshot do Cliente Android:

<img src="https://i.imgur.com/F3kZ9Vh.png" alt="plex" width="400"/>
