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

# openjdk-8 的 8u512 由 jammy-updates / jammy-security 提供
# 如需精确锁定版本，把包名写成 openjdk-8-jdk-headless=8u512-b09-0ubuntu1~22.04.1
RUN apt-get update && \
    apt-get install -y --no-install-recommends -t jammy-updates \
        openjdk-8-jdk-headless \
        ca-certificates-java && \
    rm -rf /var/lib/apt/lists/*


ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV PATH=${JAVA_HOME}/bin:${PATH}

# 构建时确认版本是否为目标版本 1.8.0_512
RUN java -version
# RUN java -version 2>&1 | grep -q '1\.8\.0_512' || (echo "JDK 版本不符" && exit 1)

# notes: 该镜像是公开镜像-不得存放任何敏感信息
# crpi-8kvyt6flnal17nk5.cn-beijing.personal.cr.aliyuncs.com/liveno/ubuntu:jammy-env
