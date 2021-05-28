FROM amd64/alpine:3.10

LABEL maintainer="snowdream <sn0wdr1am@icloud.com>"

ENV FRP_VERSION 0.36.2
ENV TZ=Asia/Shanghai

RUN cd /root \
    &&  apk add --no-cache tzdata \
    &&  ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    &&  wget --no-check-certificate -c https://github.com/fatedier/frp/releases/download/v${FRP_VERSION}/frp_${FRP_VERSION}_linux_amd64.tar.gz \
    &&  tar zxvf frp_${FRP_VERSION}_linux_amd64.tar.gz  \
    &&  cd frp_${FRP_VERSION}_linux_amd64/ \
    &&  cp frps /usr/bin/ \
    &&  mkdir -p /etc/frp \
    &&  cp frps.ini /etc/frp \
    &&  cd /root \
    &&  rm frp_${FRP_VERSION}_linux_amd64.tar.gz \
    &&  rm -rf frp_${FRP_VERSION}_linux_amd64/ 

ENTRYPOINT /usr/bin/frps -c /etc/frp/frps.ini