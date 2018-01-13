FROM securedrop-base:%TAG%

WORKDIR /app

RUN mkdir -p /var/lib/securedrop/store /var/lib/securedrop/keys
COPY ./tests/files/test_journalist_key.pub /var/lib/securedrop/keys
RUN gpg --homedir /var/lib/securedrop/keys --import /var/lib/securedrop/keys/test_journalist_key.pub

COPY static static
COPY sass sass
RUN sass --force --stop-on-error --update sass:static/css --style compressed

COPY . /app
RUN make test-config && ./manage.py reset

EXPOSE 8080 8081 5901

CMD ["./manage.py", "run"]
