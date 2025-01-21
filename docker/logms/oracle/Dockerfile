FROM rockylinux:8.9.20231119

RUN curl -sLo /dumb-init \
       https://github.com/Yelp/dumb-init/releases/download/v1.2.2/dumb-init_1.2.2_amd64
RUN chmod +x /dumb-init

COPY ./tools/start.sh /tools/start.sh
RUN chmod +x /tools/start.sh

COPY ./install_files /

EXPOSE 8080

ENTRYPOINT ["/dumb-init", "sh", "/tools/start.sh"]