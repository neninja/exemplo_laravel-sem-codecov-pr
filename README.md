# Exemplo de teste com Laravel com gh-actions

## Configuração inicial

1. Duplique `.env.example` para `.env`

```sh
cp .env.example .env
```

2. Baixe as dependências do composer

```sh
docker run --rm -u "$(id -u):$(id -g)" -v $(pwd):/var/www/html -w /var/www/html laravelsail/php81-composer:latest composer install --ignore-platform-reqs
```

3. Suba o ambiente

```sh
./vendor/bin/sail up -d
```

> Pode ser parado com ``./vendor/bin/sail down``

4. Crie a chave de criptografia

```sh
./vendor/bin/sail artisan key:generate
```

## Teste

1. Caso a configuração inicial tenha recém sido feita, o ambiente já está ativo, do contrário suba-o
2. Execute os testes com coverage
```sh
./vendor/bin/sail test --coverage --min=10
```
