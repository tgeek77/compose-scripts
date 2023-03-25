FROM opensuse/tumbleweed

# install base packages
RUN zypper ref && zypper -n install go git

RUN mkdir -p "/var/log/molly/"
RUN touch "/var/log/molly/access.log"
RUN touch "/var/log/molly/error.log"
RUN mkdir -p "/srv/gemini/"

RUN go install tildegit.org/solderpunk/molly-brown@latest
RUN mv /root/go/bin/molly-brown /usr/local/bin

COPY molly.conf /etc/
COPY cert.pem /
COPY key.pem /

CMD /usr/local/bin/molly-brown -c /etc/molly.conf

VOLUME  ["/srv/gemini"]


EXPOSE 1965/tcp
