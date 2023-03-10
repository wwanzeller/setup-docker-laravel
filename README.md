# Setup Docker Para Projetos Laravel:
Por [Wenderson Wanzeller](https://www.linkedin.com/in/wenderson-wanzeller/)

### Passo a passo:
Clone o repositório de setup:
```sh
git clone https://github.com/wwanzeller/setup-docker-laravel.git
```

Clone o repositório Laravel:
```sh
git clone https://github.com/laravel/laravel.git app-laravel
```

Copie os ficheiros docker-compose.yml, Dockerfile e o diretório docker/ para o seu projeto Laravel:
```sh
cp -rf setup-docker-laravel/* app-laravel/
```
```sh
cd app-laravel/
```
Remova o versionamento do repositório Laravel:
```sh
rm -rf .git/
```
Crie as variáveis de ambiente .env no Laravel:
```sh
cp .env.example .env
```
Atualize as variáveis de ambiente no ficheiro (.env) do Laravel conforme exemplo do repositório de setup (
env.setup.txt)

```dosini
APP_NAME="Sua Aplicação"
APP_URL=http://localhost

DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=nome_que_desejar_db
DB_USERNAME=nome_usuario
DB_PASSWORD=senha_aqui
DB_ROOT_PASSWORD=senha_aqui

CACHE_DRIVER=redis
QUEUE_CONNECTION=redis
SESSION_DRIVER=redis

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379
```

Suba os containers do projeto:
```sh
docker-compose up -d
```

Acesse o container:
```sh
docker-compose exec app bash
```

Instale as dependências do projeto:
```sh
composer install
```

Gere a key do projeto Laravel:
```sh
php artisan key:generate
```

Acesse o projeto:
[http://localhost](http://localhost)
