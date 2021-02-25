FROM golang:1.14-alpine

ENV PORT=4001
EXPOSE 4001

COPY . /src
WORKDIR /src

RUN go build 
CMD ["./vuego-demoapp"]
