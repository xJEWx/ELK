FROM debian:12

RUN useradd -ms /bin/bash elasticsearch

COPY elasticsearch-8.10.2-amd64.deb .
COPY ./config/elasticsearch.yml /tmp/
#COPY ./config/jvm.options /tmp/

# Create directories for Elasticsearch data and logs
RUN mkdir -p /usr/share/elasticsearch/data /usr/share/elasticsearch/logs

# Set permissions for the directories
RUN chown -R elasticsearch:elasticsearch /usr/share/elasticsearch


RUN dpkg -i ./elasticsearch-8.10.2-amd64.deb | grep -oP "The generated password for the elastic built-in superuser is : \K.*" > /tmp/pass.txt
#RUN mv /tmp/elasticsearch.yml /etc/elasticsearch/elasticsearch.yml
#RUN mv /tmp/jvm.options /etc/elasticsearch/elasticsearch.yml
#USER elasticsearch

#CMD ["elasticsearch"]
#CMD ["/usr/share/elasticsearch/bin/elasticsearch", "--quiet"]
CMD ["/usr/share/elasticsearch/bin/elasticsearch", "-E", "path.conf=/etc/elasticsearch"]
