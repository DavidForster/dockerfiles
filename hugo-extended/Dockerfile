# Build
FROM alpine:3.10 AS build

ARG HUGO_VERSION="0.58.3"

RUN apk add --no-cache git go g++ \
    && mkdir $HOME/src \
    && cd $HOME/src \
    && git clone --branch v${HUGO_VERSION} https://github.com/gohugoio/hugo.git \
    && cd hugo  \
    && go install --tags extended \
    && /root/go/bin/hugo version

# Run
FROM alpine:3.10

RUN apk add --no-cache ca-certificates libstdc++ libgcc

COPY --from=build /root/go/bin/hugo /usr/local/bin/hugo

EXPOSE 1313
