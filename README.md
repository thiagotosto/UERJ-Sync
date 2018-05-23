# UERJ-Sync
Esse é um projeto pessoal simples que faz o a sincronização de arquivos em máquinas distinas através de um repositório remoto. O mesmo nasceu de uma pequena necessidade pessoal na faculdade. Diz respeito mais sobre a configuração do ambiente no Linux do que do código em si que está nesse github.

A sincronização do repositório para máquina é feita ao se logar,  e a sincronização no caminho inverso é feita em tempo real através da monitorção do gitwatch.

Como o projeto tinha como objetivo resolver o problema de uma pessoa acessar computadores diferentes, e assim fazer a sincronização automática dos arquivos editados, ele não busca resolver concorrência de commits das máquinas periféricas no repositório remoto.

## Pacotes

É necessário a instalação dos seguintes pacotes:

* gitwatch. (https://github.com/gitwatch/gitwatch)
* git. (https://git-scm.com/)

## Diretórios

### bin
Diretório bin não é um diretório que aparece no github, porém ele é necessário para o projeto. Ele guarda, como usual, os executáveis utilizados no projeto.

### bin-mask
O diretório bin-mask guarda as máscaras dos arquivos executáveis para que sejam configuradas conforme seu ambiente.

## Arquivos

### bin/set_gitwatch.sh
Esse arquivo é responsável por realizar o pull do repositório e lançar o gitwatch para monitorar mudanças.

## Configuração

Com a configuração de seu repositório remoto preferido(github, amazon, bitbucket), siga os passos a seguir.

### Criando bin/set_gitwatch.sh

Pule para dentro do seu diretório que vai ser sincronizado e copie a máscara do arquivo para o bin/.

    cd <SEU DIRETÓRIO>
    mkdir bin
    cp bin-mask/set_gitwatch.sh.mask bin/set_gitwatch.sh
    
Edite o arquivo subtituindo o conteúdo da variável PROJECT_HOME para o caminho do sua pasta sincronizada.

    #!/bin/bash

    PATH=<PATH OF REPOSITORY> # seu caminho!!!

    cd $PATH
    git pull origin master &
    gitwatch -p origin -b master $PATH &

Em seguida dê permissão para que ele rode:

    chmod +x bin/set_gitwatch.sh

### Configurando set_gitwatch.sh para rodar ao se logar

Agora é preciso configurar o set_gitwatch.sh para rodar sempre que se logar na máquina.

Edite ou crie caso não exista o arquivo .bashrc no seu diretório home e inclua no final o comando que rode o arquivo set_gitwatch.sh:

    <CAMINHO DO SEU DIRETÓRIO>/bin/set_gitwatch.sh


    
