FROM crpi-8kvyt6flnal17nk5.cn-beijing.personal.cr.aliyuncs.com/liveno/ubuntu:jammy-develop

LABEL description="ADD Java And Python3 Env"

ENV DEBIAN_FRONTEND=noninteractive \
    LANG=C.UTF-8

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        libgcc-s1 \
        libstdc++6 \
        libc6 \
        libc6-dev \
        ripgrep \
        python3-full python3-venv python3-pip python3-dev \
        cron \
        tzdata && \
    rm -rf /var/lib/apt/lists/*

# Oracle JDK 8（OTN 许可，apt 源里没有，需从官网下载 tarball 放到本 Dockerfile 同目录）
# 下载页: https://www.oracle.com/java/technologies/downloads/#java8  （需先接受许可）
COPY jdk-8u512-linux-x64.tar.gz /tmp/jdk8.tar.gz
RUN mkdir -p /opt/jdk8 && \
    tar -xzf /tmp/jdk8.tar.gz -C /opt/jdk8 --strip-components=1 && \
    rm -f /tmp/jdk8.tar.gz

ENV JAVA_HOME=/opt/jdk8
ENV PATH=${JAVA_HOME}/bin:${PATH}

# 构建时确认版本 1.8.0_512
RUN java -version && \
    java -version 2>&1 | grep -q '1\.8\.0_512' || (echo "JDK 版本不符" && exit 1)

# notes: 该镜像是公开镜像-不得存放任何敏感信息
# crpi-8kvyt6flnal17nk5.cn-beijing.personal.cr.aliyuncs.com/liveno/ubuntu:jammy-env
