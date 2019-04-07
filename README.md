# Symfony dev environment

## Prepare

```
git clone <your_symfony_clone> symfony
git clone <your_symfony-docs_clone> symfony-docs
docker-compose up --build -d
```

## Run tests

```
docker-compose exec php-7.1 bash
```

### install dependencies
```
composer update
```

### run tests for the Messenger component

```
cd symfony && ./phpunit src/Symfony/Component/Messenger
```
