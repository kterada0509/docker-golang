FROM centos:7

ENV GOLANG_VERSION 1.7.6

ENV GOLANG_DOWNLOAD_URL https://golang.org/dl/go$GOLANG_VERSION.linux-amd64.tar.gz
ENV GOLANG_DOWNLOAD_SHA256 ad5808bf42b014c22dd7646458f631385003049ded0bb6af2efc7f1f79fa29ea

RUN yum update -y                                    \
    && yum install -y wget                           \
    git                                              \
    tar                                              \
    g++                                              \
    gcc                                              \
    libc6-dev                                        \
    make                                             \
    python-setuptools

RUN set -eux; \
    \
    curl -fsSL "$GOLANG_DOWNLOAD_URL" -o golang.tar.gz                \
    && echo "$GOLANG_DOWNLOAD_SHA256  golang.tar.gz" | sha256sum -c - \
    && tar -C /usr/local -xzf golang.tar.gz                           \
    && rm golang.tar.gz

ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH