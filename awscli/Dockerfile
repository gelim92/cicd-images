FROM alpine:3.10.3
LABEL maintainer="gylsky <gylswork-at-gmail-com>" \
      description="Amazon Web Services CLI image for use in CI pipelines"
ENV APK_DEPENDENCIES="bash curl git jq vim python3 make g++ docker" \
    PIP_DEPENDENCIES="awscli" \
    PATHS_TO_REMOVE="\
      /usr/include/* \
      /usr/share/man/* \
      /var/cache/apk/* \
      ~/.cache/pip/* \
      /var/cache/misc/*"
COPY ./version-info /usr/bin/
RUN apk add --update --upgrade --no-cache ${APK_DEPENDENCIES} \
    && pip3 install --upgrade pip \
    && pip3 --no-cache-dir install ${PIP_DEPENDENCIES} \
    && rm -rf ${PATHS_TO_REMOVE} \
    && chmod +x /usr/bin/version-info
WORKDIR /