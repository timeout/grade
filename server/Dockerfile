FROM golang:1.15.6 AS build
WORKDIR /src
ADD . /src
RUN go build -o /out/server .

FROM scratch AS bin
COPY --from=build /out/server /

