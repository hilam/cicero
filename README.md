# Raspador Legislativo

Repositório de testes de código para integrar, futuramente, o [Radar Legislativo](https://gitlab.com/codingrights/radarlegislativo). O objetivo é automatizar a inclusão de projetos de lei no _Radar_ de acordo com palavras chaves.

O repositório serve também para coletar dados de todos os projetos de lei em
tramitação independente de palavra chave.

## Configurações

Copie os arquivos de configuração e edite-os de acordo com o desejado:

```sh
$ cp .env.sample .env
$ cp secrets/keywords.json.sample secrets/keywords.json
```

> Não configurar a variável `KEYWORDS` faz com que o Raspador colete dados sobre
**todos** os projetos de lei em tramitação.

## Instalação em container (com Docker)

Requer [Docker](https://docs.docker.com/install/) e
[Docker Compose](https://docs.docker.com/compose/install/).

Colete os projetos de lei da Câmara e do Senado e salve os dados em um CSV com:

```sh
$ docker-compose up
```

Verifique o resultado no diretótio `data/`.

### Testes

```sh
docker-compose run --rm camara py.test
```

## Instalação local (sem Docker)

Requer [Python](https://python.org) 3.6 com [Pipenv](https://docs.pipenv.org/).

Instale as dependências e entre no _virtualenv_:

```sh
$ pipenv install
$ pipenv shell
```

Colete os projetos de lei da Câmara e do Senado e salve os dados em um CSV com:

```sh
$ scrapy crawl camara
$ scrapy crawl senado
```

Verifique o resultado no diretótio `data/`.

### Testes

```sh
py.test
```