FROM python:alpine3.7

RUN apk update && apk add nginx supervisor

RUN pip install flask gunicorn

WORKDIR app
COPY main.py .
COPY wsgi.py .
COPY flask.conf /etc/nginx/conf.d/default.conf
RUN echo "daemon off;" >> /etc/nginx/nginx.conf
RUN mkdir /etc/supervisor.d
RUN mkdir -p /run/nginx
COPY supervisord.conf /etc/supervisor.d/supervisord.ini
COPY gunicorn.conf /etc/supervisor.d/gunicorn.ini

CMD ["/usr/bin/supervisord"]
