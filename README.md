# UERJ-Sync
Esse é um projeto pessoal simples, que faz o a sincronização de arquivos em máquinas distinas através de um repositório remoto. Projeto nasceu de uma pequena necessidade pessoal na faculdade. O projeto é mais sobre configuração do ambiente no Linux do que do código em si que está nesse repositório.

A sincronização do repositório para máquina é feita ao se logar,  e a sincronização da máquina para o repositório remoto é feita em tempo real através da monitorção do gitwatch.

Como o projeto tinha como objetivo resolver o problema de uma pessoa acessar computadores diferentes, ele não busca resolver concorrência de commits das máquinas periféricas no repositório remoto.

## Pacotes

É necessário a instalação dos seguintes pacotes:

* gitwatch. (https://github.com/gitwatch/gitwatch)
* git. (https://git-scm.com/)

## Diretórios

### bin
Diretório bin não é um diretório que aparece no github, porém ele é necessário para o projeto. Ele guarda, como usual, os executáveis utilizados no projeto.

### bin-mask
O diretório bin-mask guarda as máscaras dos arquivsos executáveis para que sejam configuradas conforme seu ambiente.

## Arquivos

### bin/set_gitwatch.sh
Esse arquivo é responsável por realizar o pull do repositório e lançar o gitwatch para monitorar mudanças.
