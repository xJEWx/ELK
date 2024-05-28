FROM debian:latest
RUN apt-get update && apt-get install -y wget gnupg
ADD https://disk.yandex.ru/d/iTeGunblJU8UEg /tmp/elasticsearch-8.10.2-amd64.deb
RUN dpkg -i /tmp/elasticsearch-8.10.2-amd64.deb
RUN rm /tmp/elasticsearch-8.10.2-amd64.deb
RUN mkdir -p /etc/elasticsearch
COPY /config/elasticsearch.yml /etc/elasticsearch/elasticsearch.yml
RUN groupadd -g 1000 elasticsearch || true && useradd -u 1000 -g elasticsearch -s /bin/bash -m elasticsearch || true
RUN chown -R elasticsearch:elasticsearch /etc/elasticsearch /var/lib/elasticsearch /var/log/elasticsearch
USER elasticsearch
EXPOSE 9200 9300
CMD ["/usr/share/elasticsearch/bin/elasticsearch"]
