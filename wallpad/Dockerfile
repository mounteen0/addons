# ARG BUILD_FROM="alpine:latest"  <-  원래 이 줄은 그대로 두세요.
ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Copy data for add-on
COPY run.sh /
COPY js /js

# Install requirements for add-on
RUN apk update && apk add --no-cache glibc-compat && \  # glibc-compat 명시적 설치 (수정 1 적용)
    apk add --no-cache jq npm make gcc g++ python3 linux-headers udev && \
    npm init -f && \
    npm install mqtt && \
    npm install serialport --build-from-source=serialport

WORKDIR /share

RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
