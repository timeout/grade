FROM golang:1.15.6 AS build

ENV GO111MODULE=on

WORKDIR /src

RUN go get github.com/cespare/reflex

COPY go.mod .
COPY go.sum .
RUN go mod download

COPY . .
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build .

FROM scratch AS bin
COPY --from=build /src/server /app/

EXPOSE 8080
CMD ["/app/server"]
