FROM --platform=linux/amd64  rockylinux:8.9.20231119

RUN curl -sLo /dumb-init \
       https://github.com/Yelp/dumb-init/releases/download/v1.2.2/dumb-init_1.2.2_amd64
RUN chmod +x /dumb-init

COPY ./tools/start.sh /tools/start.sh
RUN chmod +x /tools/start.sh

COPY ./install_files /

RUN yum install net-tools -y
RUN yum install which -y
RUN yum install procps -y 
RUN yum install ncurses -y 

EXPOSE 8080

ENTRYPOINT ["/dumb-init", "sh", "/tools/start.sh"]