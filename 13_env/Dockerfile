FROM crpi-8kvyt6flnal17nk5.cn-beijing.personal.cr.aliyuncs.com/liveno/ubuntu:jammy-develop

LABEL description="ADD Java And Python3 Env"

ENV DEBIAN_FRONTEND=noninteractive \
    LANG=C.UTF-8

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        python3-full python3-venv python3-pip python3-dev \
        openjdk-8-jdk-headless \
        ca-certificates-java \
        tzdata && \
    rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=${JAVA_HOME}/bin:${PATH}


# notes: 该镜像是公开镜像-不得存放任何敏感信息
# crpi-8kvyt6flnal17nk5.cn-beijing.personal.cr.aliyuncs.com/liveno/ubuntu:jammy-env
