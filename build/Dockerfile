# stage 1 building the code
FROM golang:1.15 as builder

# don't place it into $GOPATH/bin because Drone mounts $GOPATH as volume
RUN ls -l
RUN go get github.com/golangci/golangci-lint/cmd/golangci-lint@master
RUN ls -l
WORKDIR $GOPATH/src/golangci-lint
#WORKDIR $GOPATH/src/golangci-lint
RUN ls -l
RUN go build -o /usr/bin/golangci-lint ./cmd/golangci-lint/main.go

# stage 2
FROM golang:1.15
COPY --from=builder /usr/bin/golangci-lint /usr/bin/
CMD ["golangci-lint"]
