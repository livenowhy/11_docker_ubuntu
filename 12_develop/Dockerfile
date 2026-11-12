FROM crpi-8kvyt6flnal17nk5.cn-beijing.personal.cr.aliyuncs.com/liveno/ubuntu:jammy

LABEL description="Make Ubuntu Development Environment"

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' > /etc/timezone

# ARG BUN_RUNTIME_TRANSPILER_CACHE_PATH=0
# ENV BUN_RUNTIME_TRANSPILER_CACHE_PATH=0
# 1. 安装元包
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install build-essential -y
RUN apt-get install systemd passwd openssl openssh-server openssh-client gcc vim git curl zip rar cmake sudo wget -y
RUN apt-get install util-linux -y

# 2. 配置 supervisor
RUN apt-get install supervisor -y
RUN echo_supervisord_conf > /etc/supervisord.conf
RUN echo '[include]' >> /etc/supervisord.conf && echo 'files = /etc/supervisord.d/*.ini' >> /etc/supervisord.conf
RUN supervisord -c /etc/supervisord.conf

RUN rm -rf /var/lib/apt/lists/*

WORKDIR /share
ADD run-server.sh    /share/run-server.sh
RUN chmod a+x        /share/run-server.sh
CMD ["/share/run-server.sh"]

# notes: 该镜像是公开镜像-不得存放任何敏感信息
# crpi-8kvyt6flnal17nk5.cn-beijing.personal.cr.aliyuncs.com/liveno/ubuntu:jammy-develop