FROM golang:1.14-stretch as build

ADD . /src/ticker
WORKDIR /src/ticker
RUN go build -o /bin/ticker ./services/ticker


FROM ubuntu:xenial-20210416

RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates
COPY --from=build /bin/ticker /app/
EXPOSE 8000
ENTRYPOINT ["/app/ticker"]
