FROM golang:1.9.2-alpine
WORKDIR /go/src/app

RUN apk update && apk upgrade && \
    apk add --no-cache bash git openssh mysql mysql-client && rm -f /var/cache/apk/* && \
    go get -u github.com/golang/dep/cmd/dep

ADD ./src/app /go/src/app

RUN dep ensure -vendor-only && go build -ldflags "-s -w" -o main .

CMD ["sh", "/deploy.sh"]
