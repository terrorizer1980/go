FROM golang:1.14-stretch as build

ADD . /src/webauth
WORKDIR /src/webauth
RUN go build -o /bin/webauth ./exp/services/webauth


FROM ubuntu:xenial-20201014

RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates
COPY --from=build /bin/webauth /app/
EXPOSE 8000
ENTRYPOINT ["/app/webauth"]
CMD ["serve"]
