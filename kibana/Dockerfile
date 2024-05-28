FROM debian:latest
RUN apt-get update && apt-get install -y wget gnupg
ADD kibana-8.10.2-amd64.deb /tmp/kibana-8.10.2-amd64.deb
RUN dpkg -i /tmp/kibana-8.10.2-amd64.deb || apt-get install -f -y
RUN rm /tmp/kibana-8.10.2-amd64.deb
RUN mkdir -p /etc/kibana
COPY /config/kibana.yml /etc/kibana/kibana.yml
RUN groupadd -g 1000 kibana || true && useradd -u 1000 -g kibana -s /bin/bash -m kibana || true
RUN chown -R kibana:kibana /etc/kibana /var/lib/kibana /var/log/kibana
USER kibana
EXPOSE 5601
CMD ["/usr/share/kibana/bin/kibana"]
