FROM golang:1.15.6 AS build

ENV GO111MODULE=on

WORKDIR /src
ADD . /src

RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o /out/server .

FROM scratch AS bin
COPY --from=build /out/server /app/

EXPOSE 8080
ENTRYPOINT ["/app/server"]
