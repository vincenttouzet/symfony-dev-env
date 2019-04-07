FROM python:alpine

RUN apk add --update git make

RUN pip install sphinx~=1.3.0 git+https://github.com/fabpot/sphinx-php.git

WORKDIR /var/www/sources/_build
