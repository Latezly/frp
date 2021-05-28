FROM arm32v6/alpine:3.10

LABEL maintainer="snowdream <sn0wdr1am@icloud.com>"

ENV FRP_VERSION 0.36.2
ENV TZ=Asia/Shanghai

COPY qemu-arm-static /usr/bin

RUN cd /root \
    &&  apk add --no-cache tzdata \
    &&  ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    &&  wget --no-check-certificate -c https://github.com/fatedier/frp/releases/download/v${FRP_VERSION}/frp_${FRP_VERSION}_linux_arm.tar.gz \
    &&  tar zxvf frp_${FRP_VERSION}_linux_arm.tar.gz  \
    &&  cd frp_${FRP_VERSION}_linux_arm/ \
    &&  cp frpc /usr/bin/ \
    &&  mkdir -p /etc/frp \
    &&  cp frpc.ini /etc/frp \
    &&  cd /root \
    &&  rm frp_${FRP_VERSION}_linux_arm.tar.gz \
    &&  rm -rf frp_${FRP_VERSION}_linux_arm/ 

ENTRYPOINT /usr/bin/frpc -c /etc/frp/frpc.ini