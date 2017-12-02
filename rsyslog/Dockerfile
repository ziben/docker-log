FROM jumanjiman/rsyslog
RUN sed -ri -e 's!http://dl-cdn.alpinelinux.org!https://mirrors.aliyun.com!g' /etc/apk/repositories
RUN apk update && \
    apk --no-cache add ca-certificates tzdata rsyslog-mysql=8.26.0-r0&&\
    ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" > /etc/timezone
