FROM rockylinux:8.9.20231119

RUN curl -sLo /dumb-init \
       https://github.com/Yelp/dumb-init/releases/download/v1.2.2/dumb-init_1.2.2_amd64
RUN chmod +x /dumb-init

COPY ./install_files /install_files

RUN yum install net-tools -y
RUN yum install which -y
RUN yum install procps -y 
RUN yum install ncurses -y 

COPY ./tools/start.sh /tools/start.sh
RUN chmod +x /tools/start.sh

EXPOSE 8080

RUN useradd logms
RUN mv /install_files/* /home/logms/
RUN chown logms:logms /home/logms/*

RUN ls -al /home/logms
USER logms
WORKDIR /home/logms
RUN pwd && (echo 1; echo ""; echo ""; echo ""; echo ""; echo "Y"; echo "Y") | source /home/logms/sherpa_logms_install_auto.sh oracle

USER root

ENTRYPOINT ["/dumb-init", "sh", "/tools/start.sh"]
