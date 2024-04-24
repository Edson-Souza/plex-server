# Plex no Docker

Este repositorio cria um servidor de streaming usando o Plex Media Server.

## Requerimentos

Instalar Docker

```
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
echo "deb [arch=armhf] https://download.docker.com/linux/debian \
     $(lsb_release -cs) stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list
sudo apt update && sudo apt install -y --no-install-recommends docker-ce docker-compose
```

Modifique seu docker config para que guarde os temps no disco:

```
sudo vim /etc/default/docker
# Add esta linha ao final com o caminho do docker-tmp dentro da pasta plex
export DOCKER_TMPDIR="/mnt/storage/docker-tmp"
```

## Local das midias

No arquivo '.env' estão declaradas variaveis que apontam para diretorios de midia.
Este servidor conta com 2 HDs e portando, precisa de duas variaveis.

Crie um arquivo chamado '.env' e adicione as linhas abaixo:
```
# caminho dos arquivos de midia e do servidor
MEDIA_Lenny=/media/edson/ANDROID-Lenny/
MEDIA_Famous=/media/edson/ANDROID-Famous/
```
A primeira linha é apenas um comentario.
A segunda e terceira declaram os caminhos do armazenamento.
Modifique, se necessario, o texto a partir do sinal de igual(=) para o diretorio atualizado.
É possivel modificar o nome da variavel, e lembre-se que essas variaveis são usadas pelo Docker no arquivo 'plex.yaml' e portanto deve ser verificado para fazer as devidas modificações.

## Como rodar o Plex?

Execute o comando abaixo no terminal:

`docker-compose up -d`

Use o link [localhost:32400/manege](localhost:32400/manege) para acessar o Plex.

## IMPORTANTE

Se esta tendo travamentos e pausas no streaming de midia, pra corrigir isso devemos dizer ao Plex, que nao fazer o transcode pra poupar largura de banda, entao devemos configurar os Clientes Plex (sim, devemos fazer isso em cada Cliente) para que reproduza a midia na qualidade maxima (sem fazer transcode). No Android e iPhone, as configurações são muito similares, veja a screenshot do Cliente Android:

<img src="https://i.imgur.com/F3kZ9Vh.png" alt="plex" width="400"/>
