FROM alpine:3.22

ENV TZ=Asia/Shanghai

RUN set -ex && \
    apk add --no-cache \
        bash \
        curl \
        docker \
        s6-overlay \
        tzdata && \
    rm -rf \
        /var/cache/apk/* \
        /tmp/*

COPY --chmod=755 ./rootfs /

ENTRYPOINT [ "/init" ]
