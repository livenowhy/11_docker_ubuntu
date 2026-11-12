FROM ubuntu:latest

# RUN apt-get update -y && apt-get upgrade 
RUN apt-get update -y && apt-get install -y openssh-server sudo && \
    mkdir /run/sshd && \
    echo 'root:M=uRI4Z_bKYG' | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/^#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config
    #  && \
    # echo 'export TERM=xterm-256color' >> /root/.bashrc 

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]

# 密码 M=uRI4Z_bKYG - 需要自己修改
# /usr/sbin/sshd 启动 ssh 服务
# notes: 该镜像是公开镜像-不得存放任何敏感信息
